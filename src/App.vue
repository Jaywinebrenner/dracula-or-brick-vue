<template>
  <div id="app">
      <Landing  
        v-if="navigation === 'Landing'"
        :navigate='navigate'
      />
      <!-- <div v-if="navigation === 'Landing'" class="landing-pics">
        <img src="./assets/discount-dracula.png">
        <img src="./assets/brick.png">
      </div> -->

      
      <Game
        v-if="navigation === 'Game'"
      />
  </div>
</template>

<script>
import Landing from './components/Landing.vue'
import Game from './components/Game.vue'

export default {
  name: 'App',
  components: {
    Landing,
    Game
  },
  props: {

  },
  data() {
    return {
      navigation: "Landing"
    }
  },
  methods: {
      // openAccordian() {
      //     this.isActive = !this.isActive;
      // }
      navigate(view) {
        this.navigation = view;
      }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
