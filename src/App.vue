<template>
  <div id="app">
    <nav-bar></nav-bar>
    <div class="main-container">
      <img class="main-left" src="@/assets/vue-left.svg">
      <div class="main-center">
        <img class="main-logo" src="@/assets/vue-up.svg">
        <img class="main-title" src="@/assets/logo-wordtype-white@2x.png">
        <img class="main-logo reversed" src="@/assets/vue-up.svg">
      </div>
      <img class="main-right" src="@/assets/vue-right.svg">
    </div>
    <transition name="slide-fade" v-if="this.showCondition">
      <sticky-nav-bar v-if="this.showSticky"></sticky-nav-bar>
    </transition>
    <router-view/>
    <footer-component></footer-component>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import StickyNavBar from './components/StickyNavBar.vue';
import FooterComponent from './components/FooterComponent.vue';
export default {
  components: {
    FooterComponent,
    NavBar,
    StickyNavBar,
  },
  data() {
    return {
      mainContainerHeight: window.innerHeight,
      viewWidth: window.innerWidth,
      showSticky: false,
    };
  },
  computed: {
    showCondition() {
      return this.viewWidth > 600 ? true : false;
    },
  },
  methods: {
    handleScroll(e) {
      if (window.scrollY > this.mainContainerHeight) {
        this.showSticky = true;
      } else {
        this.showSticky = false;
      }
    },
  },
  created() {
    if (window.innerWidth >= 600) {
      window.addEventListener('scroll', this.handleScroll);
    }
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
};
</script>

<style lang="scss">
@import './App.scss';
@import url('https://fonts.googleapis.com/css?family=Montserrat:500');
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.main-container {
  display: flex;
  background: linear-gradient(rgba(34, 51, 67, 0.76)), url("./assets/main-bg-image.jpg") no-repeat;
  background-attachment: fixed;
  background-size: cover;
  height: 100vh;
  width: 100vw;
  .main-left, .main-right {
    height: 100vh;
    width: 16vw;
  }
  .main-center {
    flex: 1 1 80%;
    display: flex;
    flex-direction: column;
    justify-content:space-between;
    align-items: center;
    .main-title {
      width: 49vw;
      height: 4.5vw;
    }
    .main-logo {
      height: 18vmax;
    }
    .reversed {
      transform: rotate(180deg);
    }
  }
}
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateY(-10px);
  opacity: 0;
}
</style>
