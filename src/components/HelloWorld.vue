<template>
  <div v-for="current of currencyList" :key="item.id">
    <h1>{{currency.name}}</h1>
    <img v-bind:src="logo_url"/>
  </div>
</template>

<script>
console.log("hello componet")
export default {
  name: 'HelloWorld',
  props: {
    currencyList: Array,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
