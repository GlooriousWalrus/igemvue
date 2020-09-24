<template>
  <div id="curvething" class="jebat"></div>
</template>
<script>
import Two from '@jonobr1/two.js'
import { mapState } from 'vuex'

export default {
  data() {
    return {
      two_obj: Object,
      curve: Object,
      orb: Object,
      pct: 0,
      circ2: Object,
      circ3: Object,
      resizeId: null,
    }
  },
  // get counter from vuex store
  computed: mapState(['counter']),
  watch: {
    // wait until all images are loaded after which the curve can be drawn
    counter(newCount, oldCount) {
      if (newCount === 4) {
        this.init()
        window.addEventListener('scroll', this.moveball)
      }
    },
  },
  beforeMount() {
    window.addEventListener('resize', this.handleResize)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize)
    window.removeEventListener('scroll', this.moveball)
  },
  // methods
  methods: {
    // moves the ball from 0.0 (top point) to 1.0 (bottom point) on curve
    moveball(e) {
      const curvediv = document.querySelector('#curvething')

      const top = curvediv.getBoundingClientRect().top
      const total = curvediv.getBoundingClientRect().height

      if (Math.sign(top) === -1) {
        this.pct = (Math.abs(top) + window.innerHeight / 2) / total
      } else {
        this.pct = (window.innerHeight / 2 - Math.abs(top)) / total
      }

      this.curve.getPointAt(this.pct, this.orb.translation)
      this.orb.translation.addSelf(this.curve.translation)

      this.two_obj.update()
    },

    // init two.js and start the curve drawing
    init() {
      const parentwidth = document.querySelector('.secondsection').offsetWidth
      const parentheight = this.getElementComputedValue(
        '.secondsection',
        'height'
      )
      const elem = document.querySelector('#curvething')

      this.two_obj = new Two({
        type: Two.Types.canvas,
        height: parentheight,
        width: parentwidth,
      }).appendTo(elem)

      this.createCurve()
    },

    // shorthand function for getting computedstyle values, returns int
    getElementComputedValue(el, what) {
      return parseInt(
        window
          .getComputedStyle(document.querySelector(el), null)
          .getPropertyValue(what),
        10
      )
    },

    // wait till the user finishes resizing, then resize
    handleResize() {
      window.clearTimeout(this.resizeId)
      this.resizeId = window.setTimeout(this.doResize, 500)
    },

    doResize() {
      const parentwidth = document.querySelector('.secondsection').offsetWidth
      const parentheight = this.getElementComputedValue(
        '.secondsection',
        'height'
      )
      this.curve.remove()
      this.orb.remove()
      this.circ3.remove()
      this.two_obj.height = parentheight
      this.two_obj.width = parentwidth
      this.createCurve()
      this.two_obj.update()

      console.log('RESIZE')
    },

    // calculate the point values for the curve and draw it
    // TODO: rewrite me!
    createCurve() {
      const parentwidth = document.querySelector('.secondsection').offsetWidth
      const parentheight = this.getElementComputedValue(
        '.secondsection',
        'height'
      )

      const text1 = document.querySelector('.text1')
      const text1paddingleft = parseInt(
        window.getComputedStyle(text1, null).getPropertyValue('padding-left'),
        10
      )
      const text1margintop = parseInt(
        window.getComputedStyle(text1, null).getPropertyValue('margin-top'),
        10
      )
      const text1marginbottom = parseInt(
        window.getComputedStyle(text1, null).getPropertyValue('margin-bottom'),
        10
      )
      const text1rightside = text1.clientWidth - 2 * text1paddingleft
      const sun = document.querySelector('#target')
      const sunheight = sun.clientHeight
      const sunmargintop = parseInt(
        window.getComputedStyle(sun, null).getPropertyValue('margin-top'),
        10
      )
      const sunmarginbottom = parseInt(
        window.getComputedStyle(sun, null).getPropertyValue('margin-bottom'),
        10
      )
      const suntotal = sunheight + sunmargintop + sunmarginbottom

      this.circ3 = this.two_obj.makeCircle(
        parentwidth / 2,
        suntotal +
          this.getElementComputedValue('.nanoyeast', 'padding-top') * 4,

        10
      )

      const nanoyeast = document.querySelector('.nanoyeast')
      const discoyeast = document.querySelector('.discoyeast')
      const lipid = document.querySelector('.lipid')
      const lipid2 = document.querySelector('.lipid2')

      if (parentwidth <= 768) {
        this.curve = this.two_obj.makeCurve(
          parentwidth / 2,
          sunmargintop * 2,

          parentwidth / 1.95,
          suntotal,

          text1rightside,
          sunheight + sunmargintop + text1margintop,

          text1rightside,
          sunheight + sunmargintop + text1margintop + text1.offsetHeight,
          // text1paddingleft,

          parentwidth / 2,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 32) * 9,

          parentwidth / 2.4,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9,

          this.getElementComputedValue('.text2', 'padding-left') / 1.5,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') / 6,

          this.getElementComputedValue('.text2', 'padding-left') / 1.75,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') / 2,

          this.getElementComputedValue('.text2', 'padding-left') / 1.2,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') * 1.1,

          parentwidth - this.getElementComputedValue('.text3', 'padding-right'),
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') +
            this.getElementComputedValue('.text2', 'margin-bottom') * 2 +
            (parentwidth / 16) * 12,

          this.getElementComputedValue('.text3', 'padding-left') * 1.15,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') +
            this.getElementComputedValue('.text2', 'margin-bottom') * 2 +
            (parentwidth / 16) * 12 +
            280,

          this.getElementComputedValue('.text3', 'padding-left') * 1.25,
          sunheight +
            sunmargintop +
            text1margintop +
            text1.offsetHeight +
            text1marginbottom +
            (parentwidth / 16) * 9 +
            this.getElementComputedValue('.text2', 'height') +
            this.getElementComputedValue('.text2', 'margin-bottom') * 2 +
            (parentwidth / 16) * 12 +
            280 +
            this.getElementComputedValue('.text3', 'height'),

          parentwidth / 2,
          parentheight,

          true
        )
      } else {
        // bigger than 768
        this.curve = this.two_obj.makeCurve(
          sun.offsetLeft + sun.offsetWidth / 2,
          sun.offsetTop + sun.offsetHeight / 2,

          parentwidth / 1.85,
          suntotal,

          parentwidth / 1.1,
          nanoyeast.offsetTop * 1.2,

          parentwidth / 1.05,
          nanoyeast.offsetTop + nanoyeast.offsetHeight,

          parentwidth / 2,
          nanoyeast.offsetTop + nanoyeast.offsetHeight * 1.2,

          discoyeast.offsetLeft + discoyeast.offsetWidth / 5,
          discoyeast.offsetTop + discoyeast.offsetHeight / 2,

          discoyeast.offsetLeft,
          discoyeast.offsetTop + discoyeast.offsetHeight * 1.5,

          lipid.offsetLeft + lipid.offsetWidth / 2,
          lipid.offsetTop + lipid.offsetHeight / 2,

          lipid2.offsetLeft + lipid2.offsetWidth / 2,
          lipid2.offsetTop + lipid2.offsetHeight / 2,

          lipid2.offsetLeft + lipid2.offsetWidth / 2.5,
          lipid2.offsetTop + lipid2.offsetHeight,

          parentwidth / 2,
          parentheight * 0.98,

          parentwidth / 2,
          parentheight,

          true
        )
      }
      this.curve.linewidth = 3
      this.curve.noFill()
      this.curve.stroke = 'white'

      this.orb = this.two_obj.makeCircle(0, 0, 15)
      this.orb.fill = this.orb.stroke = 'rgb(255, 255, 255)'
      this.orb.linewidth = 10
      this.orb.cap = this.orb.join = 'round'

      this.curve.getPointAt(this.pct, this.orb.translation)
      this.orb.translation.addSelf(this.curve.translation)

      this.two_obj.update()
    },
  },
}
</script>

<style lang="scss">
#curvething {
  // display: flex;
  z-index: 1;
  position: absolute;
  top: 0;
  width: 100%;
}

#two-2 {
  /* position: relative; */
  height: 7vw;
  width: 7vw;
  z-index: 3;
  border-radius: 50%;
  animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    box-shadow: inset 0px 0px 58px 58px white, 0 0 10px #fff;
  }
  to {
    box-shadow: inset 0px 0px 58px 58px white, 0 0 10px #fff, 0 0 20px #fff;
  }
}
</style>
