<template>
<div>
    <h1>Crypto Pricessss</h1>
    <button v-on:click="handleClick">Screen Shot</button>
    <div id="capture" style="padding: 10px; background: #f5da55">
         <h4 style="color: #000; ">Hello world!</h4>
    </div>
</div>
</template>

<script>
import html2canvas from 'html2canvas';



export default {
  name: 'HelloWorld',
  props: {
    currencyList: Array,
  },
   data() {
    return {
      name: "jerry",
   }
 },
  methods: {
      handleClick(e) {
        console.log(e.target)
        html2canvas(document.querySelector("#capture")).then(canvas => {
        document.body.appendChild(canvas)
    });
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  background-color: rgb(255, 181, 85);
  margin: 0!important;
  border: 3px solid white;
}

</style>