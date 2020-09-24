<template>
  <div class="bg3">
    <div class="thirdsection">
      <h1>How did we do it?</h1>
      <h3>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Turpis egestas
        maecenas pharetra convallis posuere morbi leo urna carestie.
      </h3>
      <b-container fluid="sm">
        <b-row>
          <b-col>
            <div class="customcircle">
              <flasks />
              <h3>Wet Lab</h3>
            </div>
          </b-col>
          <b-col>
            <div class="customcircle yellow">
              <h3>Human Practices</h3>
            </div>
          </b-col>
          <b-col>
            <div class="customcircle">
              <div class="gearcontainer">
                <gear class="leftgear small" />
                <gear class="midgear" />
                <gear class="rightgear small" />
              </div>
              <h3>Modeling</h3>
            </div>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.bg3 {
  background-color: white;
  width: 100%;
}

.thirdsection {
  // position: absolute;
  // top: 300vh;
  display: block;
  overflow: auto;
  width: 100%;
  left: 0;
  // background-color: white;
  position: relative;

  h1 {
    color: #68cbdc;
    text-align: center;
    padding-top: 15%;
  }

  h3 {
    color: #3a93ae;
    font-size: 150%;
    text-align: center;
    padding: 5% 8% 8%;
  }

  .container-sm {
    margin-bottom: 15%;
  }

  .customcircle {
    display: block;
    /* position: relative; */
    z-index: 3;
    border-radius: 50%;
    // background-color: #3a93ae;
    border-style: solid;
    border-width: 0.25vw;
    border-color: #3a93ae;
    // margin: 50px auto;
    h3 {
      font-size: 9vw;
      font-weight: bolder;
      padding-top: 0;
    }

    &:hover {
      svg.midgear {
        animation: rot 8s linear infinite;
      }

      svg.small {
        animation: rotsmall 4s linear infinite;
      }

      @keyframes rot {
        0% {
          -webkit-transform: rotate(22deg);
        }
        100% {
          -webkit-transform: rotate(382deg);
        }
      }

      @keyframes rotsmall {
        0% {
          -webkit-transform: scale(0.7) rotate(382deg);
        }

        100% {
          -webkit-transform: scale(0.7) rotate(22deg);
        }
      }

      // lab works
    }
  }

  .customcircle.yellow {
    border-color: #f9d53e;

    h3 {
      color: #f9d53e;
    }
  }

  @media only screen and (max-width: 600px) {
    .customcircle {
      height: 70vw;
      width: 70vw;
      margin: auto;
      margin-bottom: 5%;
    }
  }

  // desktop
  @media only screen and (min-width: 600px) {
    // height: 100vh;
    .container-sm {
      max-width: 100%;
    }

    .col {
      display: flex;
      justify-content: center;
    }

    h1 {
      padding-top: 5%;
      font-size: 7vw;
    }

    h3 {
      font-size: 2vw;
      padding: 2% 17% 5% 17%;
      margin-bottom: 5%;
    }

    .customcircle {
      height: 25vw;
      width: 25vw;
      h3 {
        font-size: 3.5vw;
        font-weight: bolder;
        padding-top: 0;
      }
    }
  }
  @media only screen and (min-width: 1024px) {
    width: 64vw;
    margin-left: 18vw;
    margin-right: 18vw;

    h1 {
      padding-top: 5%;
      font-size: 5vw;
    }

    h3 {
      font-size: 1.5vw;
      padding: 2% 17% 5% 17%;
      margin-bottom: 5%;
    }

    .customcircle {
      height: 15vw;
      width: 15vw;
      h3 {
        font-size: 2vw;
        font-weight: bolder;
        padding-top: 0;
      }
    }
  }
}
</style>
