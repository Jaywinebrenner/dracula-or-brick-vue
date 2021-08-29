<template>
  <div id="landing">
      <h4>Lousy Games presents:</h4>
      <p>Time to play</p>
      <h1>Dracula?</h1>
      <h6>or</h6>
      <h1>Brick?</h1>

      <div @click="navigate('Game')" class="start-button">Start</div>
  </div>
</template>

<script>



export default {
  name: 'App',
  components: {
 
  },
    props: {
        navigate: Function
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bowlby+One+SC&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bowlby+One+SC&family=Bubblegum+Sans&display=swap');

#landing {
    text-align: center;
}

#landing h1 {
    font-family: 'Bowlby One SC', cursive;
    color: #8a0303;
    padding: 0;
    margin: 0;
    font-size: 10rem;
    line-height: 1;
}

#landing h6 {
    margin: 0;
    font-size: 1rem;
}

#landing p {
    font-family: 'Bubblegum Sans', cursive;
    font-size: 2rem;
    margin: 0;
    transform: rotate(-2deg);
}

.start-button {
    border: 1px black solid;
    background-color: rgb(212, 207, 207);
    width: 200px;
    display: inline-block;
    padding: 20px;
    border-radius: 3px;
    margin-top: 30px;
}

.start-button:hover {
    transition: .4s;
    background-color: black;
    cursor: pointer;
    color: white;
}

@media only screen and (max-width: 980px) {
#landing h1 {
    font-size: 7.5rem;
    }
}

@media only screen and (max-width: 730px) {
#landing h1 {
    font-size: 6rem;
    }
}

@media only screen and (max-width: 580px) {
#landing h1 {
    font-size: 5rem;
    }
}
@media only screen and (max-width: 480px) {
#landing h1 {
    font-size: 4rem;
    }
}

</style>
