<template>
  <div class="firstsection">
    <banner />
    <bgparticles />
    <secondsection> </secondsection>
  </div>
</template>

<style lang="scss" scoped>
.firstsection {
  // height: 100vh;
  // background-color: #3a93ae;
  background: linear-gradient(
    180deg,
    rgba(58, 147, 174, 1) 20%,
    rgba(0, 79, 87, 1) 30%
  );
  display: block;
}

@media only screen and (min-width: 768px) {
  .firstsection {
    background: linear-gradient(
      180deg,
      rgba(58, 147, 174, 1) 35%,
      rgba(0, 79, 87, 1) 50%
    );
  }
}
</style>
