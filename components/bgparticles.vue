<template>
  <Particles
    id="tsparticles"
    :options="{
      interactivity: {
        detectsOn: 'window',
        events: {
          onClick: {
            enable: false,
          },
          onHover: {
            enable: true,
            mode: 'bubble',
            parallax: {
              enable: true,
              force: 20,
              smooth: 10,
            },
          },
          resize: true,
        },
      },
      background: {
        color: {
          value: 'transparent',
        },
      },
      fpsLimit: 60,
      particles: {
        color: {
          value: '#ffffff',
        },
        collisions: {
          enable: true,
        },
        move: {
          direction: 'none',
          enable: true,
          outMode: 'bounce',
          random: true,
          speed: 0.5,
          straight: false,
        },
        number: {
          density: {
            enable: true,
            value_area: 800,
          },
          value: 80,
        },
        opacity: {
          value: 0.4,
          random: true,
          anim: {
            enable: true,
            speed: 1,
            opacity_min: 0.1,
            sync: false,
          },
        },
        shape: {
          type: 'circle',
        },
        size: {
          random: true,
          value: 3,
          anim: {
            enable: true,
            speed: 2,
            size_min: 0.1,
            sync: false,
          },
        },
      },
      detectRetina: true,
    }"
  />
</template>

<style lang="scss">
#tsparticles {
  position: fixed;
  top: 0;
  height: 100vh;
  width: 100%;
  z-index: 0;
}
</style>
