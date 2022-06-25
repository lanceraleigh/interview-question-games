<template>
  <!-- ToDo List: -->
  <!-- Reverse a string -->
  <!-- Reverse a sentence ("bob likes dogs" -> "dogs likes bob") -->
  <!-- Find the minimum value in a list -->
  <!-- Find the maximum value in a list -->
  <!-- Calculate a remainder (given a numerator and denominator) -->
  <!-- Return distinct values from a list including duplicates (i.e. "1 3 5 3 7 3 1 1 5" -> "1 3 5 7") -->
  <!-- Return distinct values and their counts (i.e. the list above becomes "1(3) 3(3) 5(2) 7(1)") -->
  <!-- Given a string of expressions (only variables, +, and -) and a set of variable/value pairs (i.e. a=1, b=7, c=3, d=14) return the result of the expression ("a + b+c -d" would be -3). -->
  <!-- FizzBuzz Game -->
  <FizzBuzz />
  <!-- Done -->
</template>

<script>
import FizzBuzzVue from "./components/FizzBuzz.vue";
export default {
  name: "App",
  components: {
    FizzBuzz: FizzBuzzVue,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #333;
  color: #8e9e31;
  margin: 0;
  padding: 1rem;
}
</style>
