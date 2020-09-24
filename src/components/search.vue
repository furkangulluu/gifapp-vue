<template>
  <div class="search">
    <p>gif.com</p>
    <input type="text" v-model="query" @keypress.enter="handleSearch"/>
    <button v-on:click="handleSearch">Search</button>
  </div>
</template>

<script>
export default {
    data(){
        return{
            query:''
        }
    },
    methods: {
        handleSearch(){
            this.$emit('SearchRequested',this.query);
        }
    }
};
</script>

<style scoped>
.search input{
    padding: 0 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    height: 35px;
    width: 400px;
}
.search p{
    font-family: 'Times New Roman';
    font-size: 40px;
}

.search button{
    padding: 5px 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #4183c4;
    color: #ffffff;
    height: 37px;
}
</style>