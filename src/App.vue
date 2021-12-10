<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld currencyList={currencyList} />

</template>

<script>

import axios from 'axios'
import HelloWorld from './components/HelloWorld.vue'
const API_KEY = 'd5cdaac83979c51ad4c168671ad8f76b40200e50'
const currencyList = []
function sendData(crypto) {
  const jsonData = JSON.stringify(crypto)
    axios.post("http://localhost:5000", jsonData, {
      headers: {'Content-Type': 'application/json'}
  })
    .then((response) => {
      console.log(response.data)
      currencyList.push(response.data) 
    })
    .catch((error) =>{
      alert(error, "error")
    })

}
function filterData(crypto) {
  const allData = []
  crypto.data.map(curr => {
    const cryptoData = {}
      cryptoData[curr.name] = curr.name
      cryptoData.price = Number(curr.price).toFixed(2)
      cryptoData.logo = curr.logo_url
    allData.push(cryptoData)
  })
  sendData(allData)
}

export default {
  components: {
    HelloWorld
 },
  setup() {
     axios.get(`https://api.nomics.com/v1/currencies/ticker?key=${API_KEY}&ids=SOL,XTZ, ALGO&interval=1&per-page=100&page=1`)
      .then((response) => {
        filterData(response)
        console.log('Crypto response', response);
      })
      .catch((error) =>{
        alert(error);
      });
  }
}




</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
