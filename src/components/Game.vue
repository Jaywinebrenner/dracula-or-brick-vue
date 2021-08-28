<template>
  <div id="game">

      <div v-if="step === 'one'" class='step-one'>
          <p>What is behind this curtain?</p>
            <img class="curtain" src="../assets/curtain.jpg">
            <h1 @click="pickDracula()">Dracula?</h1>
            <p>or</p>
            <h1 @click="pickBrick()"> Brick?</h1>
      </div>

  </div>
</template>

<script>


export default {
  name: 'Game',
  components: {
 
  },
  props: {
      navigate: Function

  },
  data() {
    return {
        step: "one"
    }
  },
  methods: {

      pickDracula() {
          this.step = "two"
      },
      pickBrick() {
          this.step = "two"
      }

  },
}
</script>

<style>

#game h1 {
    font-family: 'Bowlby One SC', cursive;
    color: #8a0303;
    padding: 0;
    margin: 0;
    font-size: 6rem;
    line-height: 1;
    cursor: pointer;
}

#game h1:hover {
    font-family: 'Bowlby One SC', cursive;
    color: #5c0707;
    padding: 0;
    margin: 0;
    font-size: 6rem;
    line-height: 1;
    cursor: pointer;
    transition: .3s;
}

#game p {
    font-family: 'Bubblegum Sans', cursive;
    font-size: 2rem;
    margin: 0;

}

.curtain {

}

</style>
