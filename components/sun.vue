<template>
  <div id="target">
    <h1 id="abstractheader">Abstract</h1>
  </div>
</template>

<style lang="scss">
#target {
  // position: absolute;
  // top: calc(50% - 150px);
  // left: calc(50% - 150px);
  position: relative;
  margin: 100px auto;
  margin-bottom: 10%;
  z-index: 3;
  border-radius: 50%;
  background-color: #ffffcc;
  box-shadow: inset 0 0 50px #ffffcc, inset 20px 0 80px #f4dd35,
    inset -20px 0 80px #ffffcc, inset 20px 0 300px #f4dd35,
    inset -20px 0 300px #f4dd35, 0 0 50px #f4dd35, -10px 0 80px #f4dd35,
    10px 0 80px #f4dd35;
}

#abstractheader {
  position: relative;
  -webkit-user-select: none; /* Chrome all / Safari all */
  -moz-user-select: none; /* Firefox all */
  -ms-user-select: none; /* IE 10+ */
}

/* for mobile phones: */
#target {
  // top: 40vw;
  width: 40vw;
  height: 40vw;
}

#abstractheader {
  font-size: 25vw;
  right: 58%;
  top: 20%;
  text-shadow: 2px 2px 5px rgba(0, 79, 87, 1);
}

/* For desktop: */
@media only screen and (min-width: 768px) {
  #target {
    width: 15vw;
    height: 15vw;
  }

  #abstractheader {
    font-size: 9vw;
    right: 55%;
    top: 3vw;
  }
}

@media only screen and (min-width: 1024px) {
  #target {
    width: 10vw;
    height: 10vw;
  }

  #abstractheader {
    font-size: 6vw;
    right: 55%;
    top: 2vw;
  }
}
</style>
