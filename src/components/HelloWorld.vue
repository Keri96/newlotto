<template>
  <b-nav class="header" id="grad1" c>
    <h1 style="font-weight: 600" class="text-light navbar mx-5">
      Lottery Simulator
    </h1>
  </b-nav>
  <div style="transparent">
    <h1>11</h1>
    <h2></h2>
  </div>
  <div style="background-color: lightgray" class="container">
    <div
      style="background-color: white"
      class="d-flex m-5 rounded shadow justify-content-center"
    >
      <div class="rounded col-10">
        <h1
          style="font-weight: bold"
          class="justify-content-start col-1 m-2 my-4 text-bold"
        >
          Result
        </h1>

        <div class="mx-2 my-5 col-6 rounded p-2 green text-white">
          <table style="width: 100%">
            <tr>
              <td>
                <p class="col-6 justify-content-start p-2">
                  Number of Tickets:
                </p>
              </td>
              <td>
                <div
                  style="font-weight: bold"
                  class="col-6 justify-content-start"
                >
                  {{ numberOfTickets }}
                </div>
              </td>
            </tr>
            <tr>
              <td>
                <p class="col-6 justify-content-start p-2">Years spendt:</p>
              </td>
              <td>
                <div class="col-6 justify-content-start">
                  {{ Math.trunc(weeksSpent / 52) }}
                </div>
              </td>
            </tr>
            <tr>
              <td>
                <p class="col-6 justify-content-start p-2">Cost of tickets:</p>
              </td>
              <td>
                <div class="col-6 justify-content-start">
                  {{ numberOfTickets * 300 + " Ft" }}
                </div>
              </td>
            </tr>
          </table>

          <div class="row justify-content-start"></div>
        </div>
        <div class="m-2 rounded d-flex">
          <div class="p-4 first">
            <p class="mx-4 blueHeavyWords" style="font-weight: bold">
              2 matches
            </p>
            <h4 class="mx-4 blueHeavyWords" style="font-weight: bold">
              {{ numberOf2Matches }}
            </h4>
          </div>
          <div class="p-4 between">
            <p style="font-weight: bold" class="blueHeavyWords mx-4">
              3 matches
            </p>
            <h4 style="font-weight: bold" class="blueHeavyWords mx-4">
              {{ numberOf3Matches }}
            </h4>
          </div>
          <div class="p-4 between">
            <p style="font-weight: bold" class="blueHeavyWords mx-4">
              4 matches
            </p>
            <h4 style="font-weight: bold" class="blueHeavyWords mx-4">
              {{ numberOf4Matches }}
            </h4>
          </div>
          <div class="p-4 last">
            <p style="font-weight: bold" class="blueHeavyWords mx-4">
              5 matches
            </p>
            <h4 style="font-weight: bold" class="blueHeavyWords mx-4">
              {{ numberOf5Matches }}
            </h4>
          </div>
        </div>
        <div class="col-sm-9 col-12 my-1">
          <table class="table" style="width: 80%">
            <tr>
              <td><h5 class="m-2 left blueWords">Winning numbers</h5></td>
              <td>
                <input
                  class="col-1 input--border blueWords center"
                  maxlength="2"
                  min="1"
                  max="95"
                  size="3"
                  type="text"
                  id="win1"
                  readonly
                  :value="winnerNumbers[0]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border blueWords center"
                  maxlength="2"
                  min="1"
                  max="95"
                  size="3"
                  type="text"
                  id="win2"
                  readonly
                  :value="winnerNumbers[1]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border blueWords center"
                  maxlength="2"
                  min="1"
                  max="95"
                  size="3"
                  type="text"
                  id="win3"
                  readonly
                  :value="winnerNumbers[2]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border blueWords center"
                  maxlength="2"
                  min="1"
                  max="95"
                  size="3"
                  type="text"
                  id="win4"
                  readonly
                  :value="winnerNumbers[3]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border blueWords center"
                  maxlength="2"
                  min="1"
                  max="95"
                  size="3"
                  type="text"
                  id="win5"
                  readonly
                  :value="winnerNumbers[4]"
                />
              </td>
            </tr>
            <tr>
              <td><h5 class="m-2 left blueWords">Your numbers:</h5></td>
              <td>
                <input
                  class="col-1 input--border center blueWords"
                  maxlength="2"
                  max="95"
                  size="3"
                  type="text"
                  v-bind:readonly="isReadOnly"
                  :value="yourNumbers[0]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border center blueWords"
                  maxlength="2"
                  max="95"
                  size="3"
                  type="text"
                  v-bind:readonly="isReadOnly"
                  :value="yourNumbers[1]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border center blueWords"
                  maxlength="2"
                  max="95"
                  size="3"
                  type="text"
                  v-bind:readonly="isReadOnly"
                  :value="yourNumbers[2]"
                />
              </td>
              <td>
                <input
                  class="col-1 input--border center blueWords"
                  maxlength="2"
                  max="95"
                  size="3"
                  type="text"
                  v-bind:readonly="isReadOnly"
                  :value="yourNumbers[3]"
                />
              </td>
              <td>
                <input
                  class="input--border center blueWords"
                  maxlength="2"
                  max="95"
                  size="3"
                  type="text"
                  v-bind:readonly="isReadOnly"
                  :value="yourNumbers[4]"
                />
              </td>
            </tr>
          </table>
          <table class="table">
            <tr>
              <td>
                <h5 class="blueWords left m-2">Play with random numbers:</h5>
              </td>
              <td>
                <input
                  class="largerCheckbox"
                  style="height: 50px"
                  type="checkbox"
                  v-model="isReadOnly"
                  id="randomCheck"
                  ref="checkbox"
                />
              </td>
            </tr>
          </table>
        </div>

        <div>
          <h5 class="blueWords left m-3">Speed</h5>
          <input
            type="range"
            min="1"
            max="1000"
            color=""
            id="range3"
            ref="rangeSlider"
            class="range2"
            v-model="rangeValue"
          />
        </div>
        <div class="row p-3 m-2 justify-content-around">
          <button @click="startLotto" class="btn col-3 m-2 btn-outline-success">
            Start
          </button>
          <button @click="stopLotto" class="btn col-3 m-2 btn-outline-success">
            Stop
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

//////////////////////////////////////////////////////////////////SCRIPT/////////////////////////////////////////////////////////////////

<script>
export default {
  name: "HelloWorld",

  props: {
    msg: String,
  },

  data() {
    return {
      winnerNumbers: [],
      yourNumbers: [],
      isReadOnly: false,
      numberOfTickets: 0,
      yearsSpent: 0,
      weeksSpent: 0,
      costOfTickets: 0,
      numberOf2Matches: 0,
      numberOf3Matches: 0,
      numberOf4Matches: 0,
      numberOf5Matches: 0,
      randomInterval: null,
      Interval: null,
      rangeValue: document.getElementById("range3"),
      checkbox: document.getElementById("randomCheck"),
    };
  },
  methods: {
    //check the checkbox status

    randomChecked() {
      let checkbox = document.getElementById("randomCheck");
      let inp1 = document.getElementById("win1");
      let inp2 = document.getElementById("win2");
      let inp3 = document.getElementById("win3");
      let inp4 = document.getElementById("win4");
      let inp5 = document.getElementById("win5");
      if (checkbox.checked == true) {
        console.log("csekkolva");
        inp1.setAttribute("readonly", true);
        inp2.setAttribute("readonly", true);
        inp3.setAttribute("readonly", true);
        inp4.setAttribute("readonly", true);
        inp5.setAttribute("readonly", true);
      } else {
        inp1.removeAttribute("readonly");
        inp2.removeAttribute("readonly");
        inp3.removeAttribute("readonly");
        inp4.removeAttribute("readonly");
        inp5.removeAttribute("readonly");
      }
    },

    //generate random number for you

    randomForYou() {
      this.yourNumbers = [];
      const crypto = window.crypto;
      const cryptoArray = new Uint32Array(5);
      crypto.getRandomValues(cryptoArray);
      for (let i = 0; i < 5; i++) {
        // Map the values to the desired range (1 to 95)
        const randomNumber = (cryptoArray[i] % 95) + 1;
        if (!this.yourNumbers.includes(randomNumber)) {
          this.yourNumbers.push(randomNumber);
        }
      }
      console.log(this.yourNumbers);
      return this.yourNumbers;
    },

    //generate random winner number

    randomWinner() {
      this.winnerNumbers = [];
      const crypto = window.crypto;
      const cryptoArray = new Uint32Array(5);
      crypto.getRandomValues(cryptoArray);

      for (let i = 0; i < 5; i++) {
        const randomBuffer = new Uint32Array(1);
        crypto.getRandomValues(randomBuffer);
        const randomNumber = (randomBuffer[0] % 95) + 1;
        this.winnerNumbers.push(randomNumber);
      }

      console.log(this.winnerNumbers);
      return this.winnerNumbers;
    },

    //start the application

    startLotto() {
      let rangeValue = document.getElementById("range3").value;
      console.log(rangeValue);
      console.log("mikodik geca");
      if (this.$refs.checkbox.checked == true) {
        this.randomInterval = setInterval(
          this.playRandomLotto,
          this.rangeValue
        );
      } else {
        this.Interval = setInterval(this.playLotto, rangeValue);
      }
    },

    playRandomLotto() {
      this.yourNumbers.splice(0);
      this.winnerNumbers.splice(0);
      this.weeksSpent++;
      this.numberOfTickets++;
      this.randomForYou();
      this.randomWinner();
      this.searchForMatch();
    },

    searchForMatch() {
      if (this.winnerNumbers.length !== 5 || this.yourNumbers.length !== 5) {
        console.log("Both arrays must have exactly 5 numbers.");
        return;
      }
      // Check for matches
      let matches = 0;
      for (let i = 0; i < 5; i++) {
        if (this.yourNumbers.includes(this.winnerNumbers[i])) {
          matches++;
        }
      }
      // Log the result
      if (matches === 2) {
        console.log("You got 2 matches!");
        this.numberOf2Matches++;
      } else if (matches === 3) {
        console.log("You got 3 matches!");
        this.numberOf3Matches++;
      } else if (matches === 4) {
        console.log("You got 4 matches!");
        this.numberOf4Matches++;
      } else if (matches === 5) {
        console.log("You got 5 matches!");
        this.numberOf5Matches++;
      } else {
        this.matchMessage = "No matches found.";
      }
    },

    playLotto() {
      //number of tickets ++

      this.winnerNumbers.splice(0);
      this.weeksSpent++;
      this.numberOfTickets++;

      this.randomWinner();
      this.searchForMatch();
    },

    //stop it

    stopLotto() {
      console.log("ezismukodik");
      if (this.$refs.checkbox.checked == true) {
        clearInterval(this.randomInterval);
      } else {
        clearInterval(this.Interval);
      }
    },
  },
};
</script>

//////////////////////////////////////////////////////////////////STYLE/////////////////////////////////////////////////////////////////

<style scoped>
#grad1 {
  height: 70px;
  background-color: red; /* For browsers that do not support gradients */
  background-image: linear-gradient(
    to right,
    rgb(153, 222, 186),
    rgb(250, 250, 191)
  );
}

.header {
  position: fixed; /* fixing the position takes it out of html flow - knows
                   nothing about where to locate itself except by browser
                   coordinates */
  left: 0; /* top left corner should start at leftmost spot */
  top: 0; /* top left corner should start at topmost spot */
  width: 100vw; /* take up the full browser width */
  z-index: 200; /* high z index so other content scrolls underneath */
  height: 100px;
}

.blueWords {
  color: rgb(31, 16, 113);
  font-weight: 500;
}

.blueHeavyWords {
  color: rgb(31, 16, 113);
  font-weight: 900;
}

input[type="checkbox"] {
  accent-color: white;
  border-color: solid grey;
}

input[type="range"] {
  /* removing default appearance */
  -webkit-appearance: none;
  appearance: none;
  /* creating a custom design */
  width: 100%;
  cursor: pointer;
  outline: none;
  /*  slider progress trick  */
  overflow: hidden;
  border-radius: 16px;
}

/* Track: webkit browsers */
input[type="range"]::-webkit-slider-runnable-track {
  height: 15px;
  background: #ccc;
  border-radius: 16px;
}

/* Track: Mozilla Firefox */
input[type="range"]::-moz-range-track {
  height: 15px;
  background: #ccc;
  border-radius: 16px;
}

/* Thumb: webkit */
input[type="range"]::-webkit-slider-thumb {
  /* removing default appearance */
  -webkit-appearance: none;
  appearance: none;
  /* creating a custom design */
  height: 15px;
  width: 15px;
  background-color: #fff;
  border-radius: 50%;
  border: 2px solid rgb(153, 222, 186);
  /*  slider progress trick  */
  box-shadow: -407px 0 0 400px rgb(153, 222, 186);
}

/* Thumb: Firefox */
input[type="range"]::-moz-range-thumb {
  height: 15px;
  width: 15px;
  background-color: #fff;
  border-radius: 50%;
  border: 1px solid rgb(153, 222, 186);

  box-shadow: -407px 0 0 400px rgb(153, 222, 186);
}

.largerCheckbox {
  transform: scale(3);
}

.table {
  line-height: 14px;
}

.green {
  background-color: rgb(153, 222, 186);
}

.input--border {
  border: 2px solid rgb(153, 222, 186);
  box-shadow: 3px 2px 5px lightgray;
  border-radius: 5px;
  width: 50%;
}

.center {
  text-align: center;
  font-size: smaller;
}

.left {
  text-align: left;
}

body {
  background: #e5e5e5;
  font-family: Nunito;
  font-style: normal;
  color: #020056;
}

body .lottery .lottery-numbers {
  font-weight: 400;
  font-size: 16px;
  line-height: 22px;
}

body .lottery .lottery-numbers .lottery-numbers__your {
  display: flex;
  align-items: center;
}

.custom-table {
  border-radius: 15px;
  border: 2px solid #ffffcc; /* Light yellow background color */
  line-height: 24px;
  align-items: center;
  box-shadow: 5px;
}

.first {
  border-radius: 15px;
  border: 2px solid #e7e775; /* Light yellow background color */
  line-height: 24px;
  align-items: center;
  box-shadow: -2px 2px 5px lightgray;
  border-radius: 15px 5px 5px 15px;
}

.last {
  border-radius: 15px;
  border: 2px solid #e7e775; /* Light yellow background color */
  line-height: 24px;
  align-items: center;
  box-shadow: 2px 2px 5px lightgray;
  border-radius: 5px 15px 15px 5px;
}

.between {
  border-radius: 15px;
  border: 2px solid #e7e775; /* Light yellow background color */
  line-height: 24px;
  align-items: center;
  box-shadow: 0px 2px 1px lightgray;
  border-radius: 5px 5px 5px 5px;
}

p {
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
}

.matchestd {
  text-align: center;
}

td {
  text-align: left;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #abebce;
}

.shadow {
  box-shadow: 15px 2px 1px rgb(48, 48, 48);
}
</style>
