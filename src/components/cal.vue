<template>
  <div class="hello">
    <h2>{{ msg }}</h2>
    <p>Input information about you</p>
    <input v-model="weight" placeholder="weight">
    <input v-model="meters" placeholder="meters">
    <input v-model="years" placeholder="years">

    <select v-model="gender">
      <option v-bind:value="'m'">Man</option>
      <option v-bind:value="'w'">Woman</option>
    </select>
    <button @click="checkall()">Calc</button>
    <p>{{ info }}</p>
  </div>
</template>

<script>
export default {
  name: 'cal',
  data () {
    return {
      checker: /[0-9]/,
      gender: '',
      bmr: '',
      meters: '',
      years: '',
      weight: '',
      msg: 'Metabolism calculator, BMR',
      info: '',
    }
  },
  methods: {
    checkall() {
      if(this.weight.match(this.checker) && this.meters.match(this.checker) && this.years.match(this.checker) && this.gender != '') {
        this.calccal()
      }
      else {
        this.info = 'input all data'
      }
    },
    calccal() {
      if(this.gender === 'm') {
        this.bmr = (9.99*this.weight) + (6.25 * this.meters) - (4.92 * this.years) + 5
      }
      else {
        this.bmr = (9.99*this.weight) + (6.25 * this.meters) - (4.92 * this.years) - 161
      }
      console.log(this.bmr);
      this.info = `Your BMR its = ${this.bmr}`
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
a {
  color: #42b983;
}
input {
  padding: 3px;
  border-radius: 50px;
  border: 1px solid gray;
  text-align: center;
}
</style>
