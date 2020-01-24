<template>
  <div id="app">
    <MyNav></MyNav>
    <Hud></Hud>
    <Footer></Footer>
  </div>
</template>

<script>
import Hud from './components/Hud.vue'
import MyNav from './components/MyNav.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  components: {
    Hud,
    MyNav,
    Footer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
