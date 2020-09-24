<template>
  <div class="flex-container">
    <div v-bind:key="gif.id" v-for="gif in gifs">
      <img v-bind:src="gif.images.fixed_height.url" alt="">
    </div>
  </div>
</template>

<script>
export default {
  props: ["gifs"]
};
</script>

<style scoped>
.container {
  padding: 10px;
  height: 600px;
  min-width: 1300px;
  max-width: 1500px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin: 50px auto;
  overflow-y: scroll;
  text-align: center;
}
.flex-container {
  display: flex;
  flex-wrap: wrap;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin: 50px auto;
  overflow-y: scroll;
  text-align: center;
}
.flex-container > div {
  margin: 10px;
}
.flex-container > img {
  width: 100px;
  margin: 10px;
  text-align: center;
  line-height: 75px;
  font-size: 30px;
}
</style>
