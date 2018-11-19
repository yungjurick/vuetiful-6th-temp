<template>
  <div id="app">
    <div class="main-container">
      <img class="main-logo" src="@/assets/vue-up.svg">
      <img class="main-title" src="@/assets/logo-wordtype-white@2x.png">
      <img class="main-logo reversed" src="@/assets/vue-up.svg">
    </div>
    <nav-bar></nav-bar>
    <router-view/>
    <footer-component></footer-component>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import FooterComponent from './components/FooterComponent.vue';
export default {
  components: {
    FooterComponent,
    NavBar,
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
  flex-wrap: wrap;
  justify-content: center;
  align-content: space-between;
  background: linear-gradient(rgba(34, 51, 67, 0.76)), url("./assets/main-bg-image.jpg") no-repeat;
  background-size: cover;
  height: 100vh;
  width: 100vw;
  .main-title {
    width: 49vw;
    height: 8vh;
  }
  .main-logo {
    flex: 1 1 100%;
    width: 22.4vw;
    height: 35.6vh;
  }
  .reversed {
    transform: rotate(180deg);
  }
}
.main-container:before {
    content: '';
    position: absolute;
    right: 0;
    top: 0;
    width: 0;
    height: 0;
    border: 50vh solid transparent;
    border-right: 15.6vw solid white;
}
.main-container:after {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      width: 0;
      height: 0;
      border: 50vh solid transparent;
      border-left: 15.6vw solid white;
}
</style>
