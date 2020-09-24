<template>
  <div>
    <b-navbar
      id="mainNav"
      toggleable="lg"
      type="light"
      variant="info"
      fixed="top"
      :class="[scrolling]"
    >
      <b-container fluid="md">
        <b-navbar-brand href="#">
          <img src="~/assets/img/tuit_logo.webp" height="66" />
        </b-navbar-brand>

        <b-navbar-toggle type="light" target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-item-dropdown text="Project" right>
              <b-dropdown-item href="#">Description</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Parts</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Characterization</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Design</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Results" right>
              <b-dropdown-item href="#">Results</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Modeling</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Demonstration</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Improve</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Human Practices" right>
              <b-dropdown-item href="#">Human Practices</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Public Engagement</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Collaborations</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Lab" right>
              <b-dropdown-item href="#">Notebook</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Experiments</b-dropdown-item>
              <b-dropdown-divider />
              <b-dropdown-item href="#">Safety</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      scrolling: {
        scrolled: false,
      },
      'navbar-dark': false,
    }
  },
  beforeMount() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.scrolling.scrolled = window.scrollY > 50
      this['navbar-dark'] = this.scrolling.scrolled
    },
  },
}
</script>

<style lang="scss">
.navbar {
  background-color: white !important;
  opacity: 0.4;
  // filter: alpha(opacity=50);
}

#mainNav {
  -webkit-transition: all 0.6s ease-out;
  -moz-transition: all 0.6s ease-out;
  -o-transition: all 0.6s ease-out;
  -ms-transition: all 0.6s ease-out;
  transition: all 0.6s ease-out;
}

.scrolled {
  // background: rgb(68, 68, 68); /* IE */
  // background: rgba(0, 0, 0, 0.78); /* NON-IE */
  background-color: white !important;
  opacity: 1;
}
</style>
