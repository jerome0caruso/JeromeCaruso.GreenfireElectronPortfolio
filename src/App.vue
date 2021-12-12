<template>
  <div
    class="container"
    :style="{
      'background-color': darkMode ? 'rgb(0, 0, 0)' : 'rgb(127, 193, 196)',
    }"
  >
    <div class="title">
      <h1 :style="{ color: darkMode ? 'rgb(127, 193, 196)' : 'rgb(0, 0, 0)' }">
        GreenFire
      </h1>
      <button
        class="ss-btn"
        v-on:click="handleClick"
        :style="{
          'background-color': darkMode
            ? 'rgb(127, 193, 196)'
            : 'rgb(216, 248, 250)',
        }"
      >
        ScreenShot
      </button>
      <button
        class="ss-btn"
        v-on:click="handleMode"
        :style="{
          'background-color': darkMode
            ? 'rgb(127, 193, 196)'
            : 'rgb(216, 248, 250)',
        }"
      >
        {{darkMode ? 'Light Mode' : 'Dark Mode'}}
      </button>
    </div>

    <div id="capture">
      <HelloWorld :currencyList="currencyList" :mode="this.darkMode" />
      <Twitter :mode="this.darkMode" />
      <Footer :mode="this.darkMode" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import HelloWorld from "./components/HelloWorld.vue";
import Twitter from "./components/Twitter.vue";
import Footer from "./components/Footer.vue";
import html2canvas from "html2canvas";
const API_KEY = "d5cdaac83979c51ad4c168671ad8f76b40200e50";

export default {
  components: {
    HelloWorld,
    Twitter,
    Footer,
  },
  data() {
    return {
      currencyList: [],
      darkMode: false,
    };
  },
  async created() {
    try {
      this.getData();
      //setInterval(() => this.getData(), 10000)
    } catch (error) {
      console.log(error);
    }
  },

  methods: {
    async getData() {
      const response = await axios.get(
        `https://api.nomics.com/v1/currencies/ticker?key=${API_KEY}&ids=SOL,XTZ, ALGO&interval=1&per-page=100&page=1`
      );
      const filteredData = this.filterData(response);
      this.sendData(filteredData);
    },
    sendData(crypto) {
      const jsonData = JSON.stringify(crypto);
      axios
        .post("http://localhost:5000", jsonData, {
          headers: { "Content-Type": "application/json" },
        })
        .then((response) => {
          this.currencyList = response.data;
        })
        .catch((error) => {
          alert(error, "error");
        });
    },
    handleClick() {
      html2canvas(document.querySelector("#capture")).then((canvas) => {
        canvas.setAttribute("id", "canvas");
        const link = document.createElement("a");
        link.download = "filename.png";
        const url = canvas.toDataURL();
        link.href = url;
        link.click();
      });
    },
    filterData(crypto) {
      const allData = [];
      const myName = {
        name: "Jerome Caruso",
        price: "",
        logo: "",
        id: "JC",
      };
      crypto.data.map((curr, index) => {
        const cryptoData = {};
        cryptoData.name = curr.name;
        cryptoData.price = Number(curr.price).toFixed(2);
        cryptoData.logo = curr.logo_url;
        cryptoData.id = curr.name + index;
        allData.push(cryptoData);
      });
      allData.push(myName);
      return allData;
    },
    handleMode() {
      this.darkMode = !this.darkMode;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
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
  font-family: "Poppins", sans-serif;
}
h1 {
  color: black;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  background: rgb(127, 193, 196);
  height: 100%;
}
.ss-btn {
  display: inline-block;
  background: rgb(216, 248, 250);
  padding: 0.35em 1.2em;
  border: 0.1em solid #ffffff;
  margin: 1rem 0.3rem 3rem 0;
  border-radius: 0.12rem;
  text-decoration: none;
  color: rgb(224, 133, 13);
  text-align: center;
  transition: all 0.2s;
}

.ss-btn:hover {
  color: #000000;
  background-color: rgb(71, 49, 21);
}
.btn:focus {
  outline: none;
}
.ss-btn:active {
  transform: scale(0.98);
}

.title {
  display: flex;
}
.title button {
  margin-left: auto;
}
</style>
