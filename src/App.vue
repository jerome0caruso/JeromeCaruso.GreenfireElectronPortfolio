<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>

import axios from 'axios'
const API_KEY = 'd5cdaac83979c51ad4c168671ad8f76b40200e50'

function sendData(crypto) {
  console.log(crypto)

    axios.get("http://localhost:5000")
      .then((response) => {
        console.log(response);
      })
      .catch((error) =>{
        alert(error);
      });

}
function filterData(crypto) {
  
  const allData = []
  crypto.data.map(curr => {
    const cryptoData = {}
      cryptoData[curr.name] = curr.name
      cryptoData.price = curr.price
      cryptoData.logo = curr.logo_url
    allData.push(cryptoData)
  })
  sendData(allData)
}

export default {
  
  setup() {

     axios.get(`https://api.nomics.com/v1/currencies/ticker?key=${API_KEY}&ids=SOL,XTZ, ALGO&interval=1&per-page=100&page=1`)
      .then((response) => {
        filterData(response)
        console.log(response);
      })
      .catch((error) =>{
        alert(error);
      });
  }
}
/*export default {
  name: 'App',
  components: {
    HelloWorld
  }
}*/
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
