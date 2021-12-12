<template>
  <div
    class="crypto-container"
    :style="{ 'background-color': mode ? 'rgb(0, 0, 0)' : 'rgb(255, 181, 85)' }"
  >
    <div class="eachCry" v-for="currency of currencyList" :key="currency.id">
      <h1 :style="{ color: mode ? 'rgb(255, 255, 255)' : 'rgb(0, 0, 0)' }">
        {{ currency.name }}
      </h1>
      <h2 :style="{ color: mode ? 'rgb(255, 255, 255)' : 'rgb(0, 0, 0)' }">
        {{ currency.price ? "$" + currency.price : null }}
      </h2>
      <img :src="currency.qrCode" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    currencyList: Array,
    mode: Boolean,
  },
  data() {
    return {
      name: "jerry",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2 {
  margin-top: 10px;
}
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
.crypto-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  background-color: rgb(255, 181, 85);
  margin: 0 !important;
  border: 3px solid white;
}
.eachCry {
  flex-direction: column;
  align-items: center;
  max-width: 200px;
  width: 200px;
  border: 0;
}
.eachCry img {
  margin-bottom: 1rem;
}
</style>