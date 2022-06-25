<template>
  <div>
    <h1>FIZZ BUZZ GUESSING GAME</h1>
    <h3>Welcome to the FizzBuzz Guessing Game!</h3>
    <h4>Go ahead and check the rules and let's get started:</h4>
    <ul class="instructions">
      <li>
        Certain numbers with a specific common denominator will return "Fizz"
      </li>
      <li>
        Other numbers with a specific common denominator will return "Buzz"
      </li>
      <li>
        When a number brings both of these specific denominators together, it
        will return "FizzBuzz"
      </li>
    </ul>
    <form action="" @submit.prevent="fizzBuzzMethod">
      <input
        type="text"
        v-model="numberInput"
        placeholder="Test possible numbers..."
      />
      <input type="submit" />
    </form>
    <h2 v-if="fizz">Fizz</h2>
    <h2 v-else-if="buzz">Buzz</h2>
    <h2 v-else-if="fizzBuzz">FizzBuzz</h2>
    <h2 v-else>*crickets*</h2>
    <form action="" @submit.prevent="finalAnswer" id="answerForm">
      <p v-if="fizzRight" class="success">Done</p>
      <p v-else class="waitJustAMinute">Please input your guess for Fizz:</p>
      <input
        type="text"
        v-model="fizzResponse"
        placeholder="Fizz Final Answer"
        id="fizzResponse"
      />
      <p v-if="buzzRight" class="success">Done</p>
      <p v-else class="waitJustAMinute">Please input your guess for Buzz:</p>
      <input
        type="text"
        v-model="buzzResponse"
        placeholder="Buzz Final Answer"
        id="buzzResponse"
      />
      <p v-if="fizzBuzzRight" class="success">Done</p>
      <p v-else class="waitJustAMinute">
        Please input your guess for FizzBuzz:
      </p>
      <input
        type="text"
        v-model="fizzBuzzResponse"
        placeholder="FizzBuzz Final Answer"
        id="fizzBuzzResponse"
      />
      <input type="submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "FizzBuzz",
  data() {
    return {
      fizzValue: "",
      buzzValue: "",
      fizzBuzzValue: "",
      fizz: false,
      buzz: false,
      fizzBuzz: false,
      numberInput: "",
      fizzResponse: "",
      buzzResponse: "",
      fizzBuzzResponse: "",
      fizzRight: false,
      buzzRight: false,
      fizzBuzzRight: false,
    };
  },
  methods: {
    // Utility functions
    findGCD(n1, n2) {
      n1 = Math.abs(n1);
      n2 = Math.abs(n2);
      while (n2) {
        let t = n2;
        n2 = n1 % n2;
        n1 = t;
      }
      return n1;
    },
    findLCM(n1, n2) {
      let gcd = this.findGCD(n1, n2);
      return (n1 * n2) / gcd;
    },
    differentTypes() {
      return typeof this.buzzValue;
    },
    // In use functions
    setUp() {
      this.fizzValue = Math.ceil(Math.random() * 9);
      let secondRandom = Math.ceil(Math.random() * 9);
      if (secondRandom === this.fizzValue && secondRandom >= 5) {
        this.buzzValue = secondRandom - 1;
      } else if (secondRandom === this.fizzValue && secondRandom < 5) {
        this.buzzValue = secondRandom + 1;
      } else {
        this.buzzValue = secondRandom;
      }
      this.fizzBuzzValue = this.findLCM(this.fizzValue, this.buzzValue);
    },
    fizzBuzzMethod() {
      let i = parseInt(this.numberInput, 10);
      if (i % parseInt(this.fizzBuzzValue, 10) === 0) {
        this.fizzBuzz = true;
        this.fizz = false;
        this.buzz = false;
      } else if (i % parseInt(this.fizzValue, 10) === 0) {
        this.fizz = true;
        this.buzz = false;
        this.fizzBuzz = false;
      } else if (i % parseInt(this.buzzValue, 10) === 0) {
        this.buzz = true;
        this.fizz = false;
        this.fizzBuzz = false;
      } else {
        this.fizz = false;
        this.buzz = false;
        this.fizzBuzz = false;
      }
      if (i === parseInt(this.fizzBuzzValue, 10)) {
        alert("You got the Least Common Multiple. Please Input below");
      } else if (i === parseInt(this.fizzValue, 10)) {
        alert("You got the Base Fizz Value. Please Input below");
      } else if (i === parseInt(this.buzzValue, 10)) {
        alert("You got the Base Buzz Value. Please Input below");
      }
    },
    finalAnswer() {
      if (parseInt(this.fizzResponse, 10) === parseInt(this.fizzValue, 10)) {
        this.fizzRight = true;
        document.getElementById("fizzResponse").disabled = true;
      }
      if (parseInt(this.buzzResponse, 10) === parseInt(this.buzzValue, 10)) {
        this.buzzRight = true;
        document.getElementById("buzzResponse").disabled = true;
      }
      if (
        parseInt(this.fizzBuzzResponse, 10) === parseInt(this.fizzBuzzValue, 10)
      ) {
        this.fizzBuzzRight = true;
        document.getElementById("fizzBuzzResponse").disabled = true;
      }
    },
  },
  mounted() {
    this.setUp();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#answerForm {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#answerForm input {
  max-width: 10rem;
}
#answerForm input[type="submit"] {
  margin-top: 1rem;
}
.success {
  color: #58f758;
}
.waitJustAMinute {
  color: #5252f5;
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
  color: #42b983;
}
</style>
