<template>
  <div class="centralizer">
    <div class="secondsection">
      <sun />
      <bgcurve />
      <p class="text1">
        Yeasts have the potential to be used as microbial cell factories for the
        production of lipids (biodiesel, high-value lipids, etc.). However,
        bio-production is costly compared to chemical synthesis, as it is highly
        energy-consuming for the cell and product extraction is laborious.
      </p>
      <b-img
        class="nanoyeast"
        src="~assets/img/nanoyeast.webp"
        fluid
        alt="Responsive image"
        @load="onImgload"
      />
      <p class="text2">
        To make it more competitive we engineer yeast cells that utilize light
        both as an inductor for a metabolic switch to start lipid production and
        as an energy source to drive the lipid synthesis. The cells will be
        coated by nanoparticles taht absorb light and provide additional
        electrons for the formation of NADPH, a critical cofactor for lipid
        synthesis.
      </p>
      <b-img
        class="discoyeast"
        src="~assets/img/yeast.webp"
        fluid
        alt="Responsive image"
        @load="onImgload"
      />
      <b-img
        class="lipid"
        src="~assets/img/lipid.webp"
        fluid
        alt="Responsive image"
        @load="onImgload"
      />
      <p class="text3">
        This approach allows rapid biomass accumulation before production,
        followed by light-induced expression of lipid synthesis enzymes
        resulting in the accumulation of lipid droplets. To ease the extraction
        of the lipid droplets, we introduce the inducible yeast autolysis method
        developed last year.
      </p>
      <b-img
        class="lipid2"
        src="~assets/img/lipid.webp"
        fluid
        alt="Responsive image"
        @load="onImgload"
      />
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onImgload() {
      this.$store.commit('increment')
    },
  },
}
</script>

<style lang="scss" scoped>
.secondsection {
  display: inline-block;
  // background-color: #004f57;
  left: 0;
  width: 100%;
  position: relative;
  z-index: 0;

  p {
    font-size: 135%;
    padding-left: 10%;
    padding-right: 20%;
    padding-top: 0;
  }

  p.text1 {
    margin-top: 15%;
    margin-right: 0;
    z-index: 1;
    position: relative;
    text-align: left;
  }

  p.text2,
  p.text3 {
    text-align: right;
    padding-right: 10%;
    padding-left: 20%;
    z-index: 1;
    position: relative;
  }

  img.nanoyeast {
    width: 95%;
    margin: 5% 2.5%;
    z-index: 2;
  }

  img.discoyeast {
    position: relative;
    z-index: 2;
  }

  img.lipid,
  img.lipid2 {
    position: relative;
    z-index: 2;
  }

  @media only screen and (min-width: 768px) {
    // width: 45%;

    p.text1 {
      padding: 0;
      padding-left: 5%;
      margin-top: 0;
      padding-bottom: 6%;
      width: 47%;
      text-align: right;
      padding-left: 5%;
      float: left;
    }

    img.nanoyeast {
      width: 42%;
      margin: 0;
      padding-top: 10%;
      // padding-left: 3%;
      margin-left: 3%;
      z-index: 2;
    }

    img.discoyeast {
      position: relative;
      z-index: 2;
      float: right;
      margin-top: -6%;
    }

    p.text2 {
      width: 47%;
      text-align: left;
      padding: 0;
      padding-right: 5%;
      float: right;
      margin-top: 14%;
    }

    img.lipid {
      width: 27%;
      margin-left: 20%;
      margin-right: -5%;
      margin-top: 15%;
    }

    p.text3 {
      width: 47%;
      padding: 0;
      padding-left: 5%;
      text-align: right;
      float: left;
      margin-bottom: 10%;
    }

    img.lipid2 {
      width: 48%;
      // margin-top: -10%;
    }
  }
}

@media only screen and (min-width: 1024px) {
  p {
    font-size: 80vw;
  }

  .centralizer {
    display: flex;
    justify-content: center;
  }

  .secondsection {
    max-width: 80vw;
  }
}

@media only screen and (min-width: 1280px) {
  .centralizer {
    display: flex;
    justify-content: center;
  }

  .secondsection {
    max-width: 60vw;

    p {
      font-size: 180%;
    }
  }
}
</style>
