<template>
    <div>
      <label for="celsius">Celsius:</label>
      <input type="number" id="celsius" v-model="celsius" @input="convert">
  <br>
      <label for="fahrenheit">Fahrenheit:</label>
      <input type="number" id="fahrenheit" v-model="fahrenheit" @input="convert">
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        celsius: 0,
        fahrenheit: 32
      }
    },
    methods: {
      convert() {
        if (this.celsius !== "") {
          this.fahrenheit = this.celsius * 1.8 + 32;
        } else if (this.fahrenheit !== "") {
          this.celsius = (this.fahrenheit - 32) / 1.8;
        }
      }
    }
  }
  </script>