<template>
  <div>
    <div class="everything">
      <navbar />
      <firstsection />
      <thirdsection />
      <fourthsection />
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss">
button,
button:active,
button:focus {
  outline: 0;
}

body {
  background-color: black;
}

.container {
  // margin: 0 auto;
  // min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  // margin-bottom: 10%;
}

.home {
  width: 100%;
  height: 100vh;
  background-position: center top;
  background-size: cover;
}
</style>
