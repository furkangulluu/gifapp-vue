<template>
  <div id="app">
    <search v-on:SearchRequested="handleSearch"></search>
    <p v-if="isLoading">Loading..</p>
    <preview v-bind:gifs="gifs"></preview>
  </div>
</template>

<script>
import Search from "./components/search.vue";
import Preview from "./components/preview.vue";

export default {
  name: "app",
  components: { Search, Preview },
  data() {
    return {
      isLoading: false,
      gifs: [],
      trendUrl:'https://api.giphy.com/v1/gifs/trending?api_key=1fG1IawxZ0CJwkiU5sAo5vnj9IF1v8rg&limit=15&rating=G'
    };
  },
  methods: {
    handleSearch(query) {
      console.log(query)
      this.gifs = [];
      this.isLoading = true;
      const url="https://api.giphy.com/v1/gifs/search?api_key=1fG1IawxZ0CJwkiU5sAo5vnj9IF1v8rg&q="+query+"&limit=15&offset=0&rating=G&lang=en"
      this.doQuery(query !== '' ? url : this.trendUrl)
    },
    doQuery(url){
      console.log(url)
      fetch(url)
        .then(res => {return res.json();})
        .then(res => {
          this.gifs = res.data;
          this.isLoading = false;
        });
    }
  },
  created() {
    const url=this.trendUrl
    this.doQuery(url)
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
