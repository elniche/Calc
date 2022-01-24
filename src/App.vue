<template>

<div id="app">
  <h1> Your Favorite Calculator!</h1>


   <calculator />
</div>
</template>

<script>
import calculator from './components/calculator.vue'

export default {
  name: 'App',
  components: {
    calculator
  }
}
</script>

<style>
body {
  background-image: url("gray.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  height: auto;
  background-attachment: fixed;
  
}

#app {
  text-align: center;
  
  
}

</style>
