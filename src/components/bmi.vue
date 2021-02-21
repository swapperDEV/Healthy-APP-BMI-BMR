<template>
  <div class="hello">
    <h2>{{ msg }}</h2>
    <input placeholder="input your weight" v-model="weight">
    <input placeholder="input your meters" v-model="meters">
    <button v-on:click="calcbmi()">Calculate</button>
    <p>{{ info }}</p>
  </div>
</template>

<script>
export default {
  name: 'bmi',
  data () {
    return {
      bmi: '',
      info: '',
      meters: '',
      weight: '',
      status: '',
      checker: /[0-9]/,
      msg: 'BMI Calculator'
    }
  },
  methods: {
    calcbmi() {
      if(this.meters.match(this.checker) && this.weight.match(this.checker)) {
      this.bmi = (this.weight/this.meters**2) * 10000
      this.bmi = this.bmi.toFixed(0);
      console.log(this.bmi);
      this.checkBmi()
      this.info = `Your bmi is ${this.bmi}, status: ${this.status}`
    }
      else {
        this.info = 'error'
      }
    },
    checkBmi() {
            if(this.bmi <= 16) {
                this.status = 'starvation'
            }
            else if(this.bmi >= 16.9 && this.bmi <= 18.4) {
                this.status = 'underweight'
            }
            else if(this.bmi >= 18.5 && this.bmi <= 24.9) {
                this.status = 'great weight'
            }
            else if(this.bmi >= 25 && this.bmi <= 29.9) {
                this.status = 'overweight'
            }
            else if(this.bmi >= 30 && this.bmi <= 34.9) {
                this.status = 'obesity (grade1)'
            }
            else if(this.bmi >= 35 && this.bmi <= 39.9) {
                this.status = 'obesity (grade2)'
            }
            else if(this.bmi >= 40) {
                this.status = 'obesity (grade3)'
            }
            else {
                this.status = 'error'
            }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
  color: gray;
}
input {
  padding: 3px;
  border-radius: 50px;
  border: 1px solid gray;
  text-align: center;
}
a {
  color: #42b983;
}
</style>
