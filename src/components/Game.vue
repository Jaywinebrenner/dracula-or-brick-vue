<template>
  <div id="game">
      <div class="nav-wrapper" v-if="step !== 'three'">
            <h6 class="instructions">You get 3 chances to guess 3 correct!</h6>
            <div class="nav">
                <h3 class="points">POINTS: {{points}}      </h3>
                <h3 class="points">BAD GUESSES: {{guessesLeft}}      </h3>
                <h3 class="points">YOUR GUESS: <img class="dracula-little little" v-if="guess === 'dracula'" src="../assets/discount-dracula.png"><img class="brick-little little" v-if="guess === 'brick'" src="../assets/brick.png"></h3>
            </div>
      </div>

      <div v-if="step === 'one'" class='step-one'>
          <p>What you think is in the box?</p>
            <img class="box" src="../assets/box.png">
            <h1 @click="choose('dracula')">Dracula?</h1>
            <p>or</p>
            <h1 @click="choose('brick')"> Brick?</h1>
      </div>
        <div v-if="step === 'two'">
            <h2 v-if="isRight">RIGHT!</h2>
            <h2 v-else>WRONG!</h2>
            <div @click="continueGame()" class="continue-game-button">Continue</div>
            <img class="dracula-image" v-if="correctAnswer === 'dracula'" src="../assets/discount-dracula.png">
            <img class="brick-image" v-if="correctAnswer === 'brick'" src="../assets/brick.png">
        </div>

        <div class="game-over-screen" v-if="step === 'three'">
            <h1 v-if="playerWon" class="game-over-text">YOU WON!!!</h1>
            <h1 v-if="!playerWon" class="game-over-text">YOU LOST!</h1>
            <div @click="playAgain()" class="restart-button">Play Again</div>
        </div>

        <div v-if="step === 'Loading'" class="loading-screen">

             <img class="loading-icon" src="../assets/hug.gif">
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
        step: "one",
        isDraculaVisible: false,
        isBrickVisible: false,
        isRight: null,
        isWrong: null,
        correctAnswer: null,
        guess: null,
        points: 0,
        guessesLeft: 0,
        playerWon: null,
        isLoading: false,
        isGameOver: false
    }
  },
  methods: {

      choose(draculaOrBrick) {
          this.loadScreenActive()
        //  this.step = "two";
        console.log("step in CHOSE", this.step)
         this.guess = draculaOrBrick;
          let result = Math.floor(Math.random()*10 +1)

        if(result <= 5) {
            this.correctAnswer = 'dracula'
          } else {
              this.correctAnswer = 'brick'
          }

        if(draculaOrBrick === 'dracula' && this.correctAnswer === 'dracula' || draculaOrBrick === 'brick' && this.correctAnswer === 'brick'){
            console.log("CORRECT ANSWER: ", this.correctAnswer)
            console.log("PLAYER GUESS: ", draculaOrBrick)
            this.isRight = true;
            this.points = this.points + 1;
        } else {
             console.log("CORRECT ANSWER: ", this.correctAnswer)
             console.log("PLAYER GUESS: ", draculaOrBrick)
             this.isRight = false;
            this.guessesLeft = this.guessesLeft + 1;

        }
        this.winCheck()

        // if(this.points === 3){
        //     console.log("YOU WON")
        //     this.playerWon = true;
        //     this.step = 'three';
        //     this.isDraculaVisible= false;
        //     this.isBrickVisible= false;
        //     this.isRight= null;
        //     this.isWrong= null;
        //     this.correctAnswer= null;
        //     this.guess= null;
        //     this.points= 0;
        //     this.guessesLeft= 0;
        // }
        // if(this.guessesLeft === 3){
        //     console.log("YOU LOST")
        //     this.playerWon = false;
        //     this.step = 'three';
        // }
      },
      winCheck(){
        if(this.points === 3){
            console.log("YOU WON")
            this.playerWon = true;
            this.step = 'three';
            this.isDraculaVisible= false;
            this.isBrickVisible= false;
            this.isRight= null;
            this.isWrong= null;
            this.correctAnswer= null;
            this.guess= null;
            this.points= 0;
            this.guessesLeft= 0;
            this.isGameOver = true;
        }
        if(this.guessesLeft === 3){
            console.log("YOU LOST")
            this.playerWon = false;
            this.step = 'three';
            this.isGameOver = true;
        }
      },
      continueGame(){
        this.step = "one";
        this.isDraculaVisible = false;
        this.isBrickVisible = false;
        this.guess = null;
        this.correctAnswer = null;

      },
      playAgain() {
        this.navigate("Landing")
        this.isDraculaVisible = false;
        this.isBrickVisible = false;
        this.guess = null;
        this.correctAnswer = null;
      },
      loadScreenActive() {
         
          console.log("LOAD")
          this.step = "Loading";
        setTimeout(function () {
            if(!this.isGameOver) {
                this.step = 'two';
            }
            }.bind(this), 750)
      }

  },
}
</script>

<style>

.points {
    display: inline-block;
}

.instructions {
 display: inline-block;
}

#game h1 {
    font-family: 'Bowlby One SC', cursive;
    color: #8a0303;
    padding: 0;
    margin: 0;
    font-size: 6rem;
    line-height: 1;
    cursor: pointer;
}
#game h2 {
    font-family: 'Bowlby One SC', cursive;
    color: #8a0303;
    padding: 0;
    margin: 0;
    font-size: 8rem;
}

#game h3 {
    font-family: 'Bowlby One SC', cursive;
    color: #8a0303;
    padding: 0;
    margin: 0;
    font-size: 2.5rem;
    margin-right: 20px;
}

#game h6 {
    margin: 0;
    padding: 0;
}

#game h1:hover {
    font-family: 'Bowlby One SC', cursive;
    color: #5c0707;
    padding: 0;
    margin: 0;
    line-height: 1;
    cursor: pointer;
    transition: .3s;
}

#game p {
    font-family: 'Bubblegum Sans', cursive;
    font-size: 2rem;
    margin: 0;
}
.continue-game-button {
    border: 1px black solid;
    width: 200px;
    display: block;
    margin: 0 auto;
    padding: 20px;
    border-radius: 3px;
    margin-bottom: 30px;
}

.continue-game-button:hover {
    transition: .4s;
    background-color: black;
    cursor: pointer;
    color: white;
}

.game-over-text {
    font-size: 8rem;

}

.dracula-image {
    height: 400px;
}

.box {
    height: 400px;
}

.dracula-little {
    width: 20px;
}
.brick-little {
    width: 60px;
}

.game-over-screen {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.restart-button {
    border: 1px black solid;
    width: 200px;
    display: inline-block;
    padding: 20px;
    border-radius: 3px;
    margin-top: 50px;
}

.restart-button:hover {
    transition: .4s;
    background-color: black;
    cursor: pointer;
    color: white;
}

.loading-icon {
    width: 30%;
    margin-top: 100px;
}

@media only screen and (max-width: 1200px) {
    #game h3 {
        font-size: 2rem;
        }
    }

@media only screen and (max-width: 970px) {
    #game h3 {
        font-size: 1.5rem;
        }
    }

@media only screen and (max-width: 750px) {
    #game h3 {
        display: block;
        }
        .box {
            height: 200px;
        }
        .little {
            position: absolute;
        }
        .brick-image {
            width: 20rem;;
        }
        .dracula-image {
            height: 15rem;;
        }
    }

@media only screen and (max-width: 970px) {
    #game h3 {
        font-size: 1.5rem;
    }
}   

@media only screen and (max-width: 600px) {
    #game h1 {
        font-size: 4rem;
        }
    #game h1:hover {
        font-size: 4rem;
    }
    #game h2 {
        font-size: 4rem;
        }
    #game h2:hover {
        font-size: 4rem;
    }
}
</style>
