<template>
  <div id="app">
    <img src="./assets/logo.png" height="300">
    <nav>
        <button v-on:click="actcomp = 'start', change($event)">Start</button>
        <button v-on:click="actcomp = 'bmi', change($event)" >BMI Calculator</button>
        <button v-on:click="actcomp = 'cal', change($event)">metabolism calculator</button>
    </nav>
    <transition name="slide" appear mode="out-in">
      <component :is="actcomp"></component>
    </transition>
  </div>
</template>

<script>
import start from './components/start.vue'
import cal from './components/cal.vue'
import bmi from './components/bmi.vue'

export default {
  data: function() {
    return {
      actcomp: 'start',
  }},
  name: 'App',
  components: {
    start,
    bmi,
    cal,
  },
  methods: {
    change(e) {
      e.target.style.color = 'blue'
      setTimeout(() => {
        e.target.style.color = 'gray'
      },500)
    },
  }
}
</script>

<style>
button {
  border: 3px solid wheat;
  border-radius: 50px;
  background-color: wheat;
  transition: 0.1s ease;
  color: gray;
  margin: 2px;
}
button:hover {
  color: black;
  transform: scale(1.1);
}
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.2s ease-in-out;}
.slide-enter {
  transform: translateX(-100vw);}
.slide-leave-to {
  transform: translateX(100vw);}            
#app {
  overflow: hidden;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
