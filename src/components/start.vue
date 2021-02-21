<template>
  <div class="hello">
    <h1>{{ appname }}<i class="fas fa-heartbeat"></i></h1>
    <h3>Here you can find very healthy calculators</h3>
    
  </div>
</template>

<script>
export default {
  name: 'start',
  data () {
    return {
      appname: 'Keep your fit/swapperDEV',
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-family: 'Potta One', cursive;
  font-weight: normal;
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
h3 {
      font-family: 'Potta One', cursive;
}
</style>
