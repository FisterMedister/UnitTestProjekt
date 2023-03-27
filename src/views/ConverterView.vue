<template>
    <div>
      <h1>Temperature and Metric System Converter</h1>
      <label for="fahrenheit">Fahrenheit</label>
      <input id="fahrenheit" v-model="fahrenheit" type="number">
      <br>
      <label for="celsius">Celsius</label>
      <input id="celsius" v-model="celsius" type="number">
    </div>

    <label for="inputValue">Value:</label>
    <input id="inputValue" v-model="inputValue" type="number">
    <br>
    <label for="fromUnit">From:</label>
    <select id="fromUnit" v-model="fromUnit">
      <option value="mm">mm</option>
      <option value="cm">cm</option>
      <option value="m">m</option>
      <option value="km">km</option>
    </select>
    <br>
    <label for="toUnit">To:</label>
    <select id="toUnit" v-model="toUnit">
      <option value="mm">mm</option>
      <option value="cm">cm</option>
      <option value="m">m</option>
      <option value="km">km</option>
    </select>
    <br>
    <label for="outputValue">Result:</label>
    <input id="outputValue" v-model="outputValue" type="number" disabled>
  </template>
  
  <script>
  export default {
    data() {
      return {
        fahrenheit: 0,
        celsius: 0,
        inputValue: 0,
        fromUnit: 'mm',
        toUnit: 'mm',
        outputValue: 0
      }
    },
    watch: {
      fahrenheit() {
        this.celsius = ((this.fahrenheit - 32) * 5/9).toFixed(2)
      },
      celsius() {
        this.fahrenheit = ((this.celsius * 9/5) + 32).toFixed(2)
      },

    inputValue() {
      this.convert()
    },
    fromUnit() {
      this.convert()
    },
    toUnit() {
      this.convert()
    }
    },
    methods: {
    convert() {
      let factor = 1
      switch(this.fromUnit) {
        case 'mm':
          factor /= 1000
          break
        case 'cm':
          factor /= 100
          break
        case 'km':
          factor *= 1000
          break
        default:
          break
      }
      switch(this.toUnit) {
        case 'mm':
          factor *= 1000
          break
        case 'cm':
          factor *= 100
          break
        case 'km':
          factor /= 1000
          break
        default:
          break
      }
      this.outputValue = (this.inputValue * factor).toFixed(2)
    }
  }
  }
  </script>