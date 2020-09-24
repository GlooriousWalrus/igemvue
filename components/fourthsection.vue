<template>
  <div class="fourthsection">
    <div class="cont">
      <div class="imgdiv">
        <h1>Teamwork</h1>
        <img class="brush" src="~assets/img/brushstroke.svg" />
        <b-img
          class="teampic"
          src="~assets/img/teampic.webp"
          fluid
          alt="Responsive image"
        />
      </div>
      <div class="item">
        <h3 class="makesthe">makes the</h3>
        <h3 id="dreamwork">dream work</h3>
        <b-button pill class="read" size="lg">READ MORE</b-button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.fourthsection {
  // position: absolute;
  // top: 520vh;
  // height: 100vh;
  width: 100%;
  left: 0;
  background-color: #f0f7f2;
  z-index: 3;
  position: relative;

  .imgdiv {
    background-color: #f0f7f2;

    .brush {
      position: relative;
      top: -6vw;
    }

    /* Top left text */
    h1 {
      color: #0092b0;
      position: relative;
      top: 16vw;
      // left: 14vw;
      padding-left: 15%;
      font-size: 15vw;
      z-index: 2;
      margin-bottom: 0;

      user-select: none;
    }

    .teampic {
      margin-top: -20%;
      margin-bottom: 15%;
    }
  }

  @media only screen and (min-width: 768px) {
    .imgdiv {
      margin-left: 5%;
      padding-bottom: 10%;
      flex: 2;

      .brush {
        max-width: 60%;
        top: -3vw;
        margin-left: 4.5%;
      }

      h1 {
        font-size: 6vw;
        top: 6vw;
        padding-left: 12%;
        width: 40%;
      }

      .teampic {
        // max-width: 65%;
        margin-top: -8%;
        margin-left: 0;
        margin-bottom: 0;
      }
    }

    .read {
      background-color: #ffd622;
      color: black;
      // margin-right: 5%;
      // width: 25%;
      margin: 5% 20% 0 20%;
      // height: 30%;
      border-color: #ffd622;
    }

    .makesthe {
      justify-content: center;
      justify-self: center;
      align-self: center;
      font-size: 220%;
      color: #3a93ae;
      font-weight: bold;
    }

    #dreamwork {
      font-family: 'HelloSanttiny';
      font-size: 400%;
      color: #67cbdb;
      justify-content: center;
      justify-self: center;
      align-self: center;
    }

    .cont {
      display: flex;
      flex-direction: row;
      background-color: #f0f7f2;
    }

    .item {
      display: flex;
      flex-direction: column;
      flex-basis: 100%;
      flex: 1;
      align-content: center;
      justify-content: center;
    }
  }
}
</style>

<script>
import CircleType from 'circletype'

export default {
  data() {
    return {
      text_obj: Object,
    }
  },
  mounted() {
    this.fixtext()
  },
  methods: {
    fixtext() {
      this.text_obj = new CircleType(
        document.getElementById('dreamwork')
      ).radius(666)
    },
  },
}
</script>
