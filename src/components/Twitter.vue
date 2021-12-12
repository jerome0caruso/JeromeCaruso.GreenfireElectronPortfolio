<template>
  <div
    class="main-twitter-container"
    :style="{ 'background-color': mode ? 'rgb(0, 0, 0)' : 'rgb(255, 181, 85)' }"
  >
    <div class="twitter-container">
      <a
        class="twitter-timeline"
        data-width="220"
        data-tweet-limit="2"
        data-height="10"
        href="https://twitter.com/BBCAfrica?ref_src=twsrc%5Etfw"
        >Tweets by BBCAfrica</a
      >
    </div>
    <div class="twitter-container">
      <a
        class="twitter-timeline"
        data-width="220"
        data-tweet-limit="2"
        data-height="200"
        href="https://twitter.com/ethereum?ref_src=twsrc%5Etfw"
        >Tweets by ethereum</a
      >
    </div>
  </div>
</template>
<script>
export default {
  name: "Twitter",
  props: {
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
.main-twitter-container {
  display: flex;
  background-color: rgb(255, 181, 85);
  justify-content: space-evenly;
  border: 3px solid white;
  border-top: none;
  padding: 2rem;
  flex-wrap: wrap;
}
.twitter-container {
  display: flex;
  flex-wrap: wrap;
  height: 400px;
  overflow-y: scroll;
}
</style>