<template>
  <div id="game">
      <h6>Get 5 correct without failure and you win big!</h6>

      <div v-if="step === 'one'" class='step-one'>
          <p>What is behind this curtain?</p>
            <img class="curtain" src="../assets/curtain.jpg">
            <h1 @click="pickDracula()">Dracula?</h1>
            <p>or</p>
            <h1 @click="pickBrick()"> Brick?</h1>
      </div>

        <img v-if="step === 'dracula'" src="../assets/discount-dracula.png">
        <img v-if="step === 'brick'" src="../assets/brick.png">

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
        //   this.step = "two";
          let result = Math.floor(Math.random()*10 +1)
          console.log(result)
          if(result <= 5) {
              console.log("You Won!")
              this.step = "dracula"
          }
          if(result > 5){
              console.log("You Lose!");
              this.step = "brick"
          }
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
        width: 50%;
}

</style>
