<template>
  <div class="container">
    <h1>Crypto Prices</h1>
    <HelloWorld :currencyList="currencyList" />
  </div>

</template>

<script>
import axios from 'axios'
import HelloWorld from './components/HelloWorld.vue'
const API_KEY = 'd5cdaac83979c51ad4c168671ad8f76b40200e50'

export default {
  components: {
    HelloWorld,
 },
 data() {
   return {
    currencyList: [],
   }
 },
   async created() {
    try {
      const response = await axios.get(`https://api.nomics.com/v1/currencies/ticker?key=${API_KEY}&ids=SOL,XTZ, ALGO&interval=1&per-page=100&page=1`)
      const filteredData = this.filterData(response);
      this.sendData(filteredData)
    } catch(error) {
      console.log(error);
    }
  },

methods: {
  sendData(crypto) {
    const jsonData = JSON.stringify(crypto)
      axios.post("http://localhost:5000", jsonData, {
        headers: {'Content-Type': 'application/json'}
    })
    .then((response) => {
      console.log(response.data)
      this.currencyList = response.data
    })
    .catch((error) =>{
      alert(error, "error")
    })
  },

  filterData(crypto) {
    const allData = []
    const myName = {
      name: "Jerome Caruso",
      price: 0.00,
      logo: '',
      id: "JC"
      }
    crypto.data.map((curr, index) => {
      const cryptoData = {}
        cryptoData.name = curr.name
        cryptoData.price = Number(curr.price).toFixed(2)
        cryptoData.logo = curr.logo_url
        cryptoData.id = curr.name + index
      allData.push(cryptoData)
    })
    allData.push(myName)
    return allData
  },
}
};

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;

}
.container {
  max-width: 500px;
  margin: 30px auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  background: rgb(127, 193, 196);
  height: 90vh;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
