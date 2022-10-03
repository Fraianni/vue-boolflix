<template>
  <header>
    <input class="search_bar" v-model="text_to_search" type="text" placeholder="Cerca film" @keyup.enter="$emit('search_this_text', text_to_search)">
    <h1>BOOLFLIX</h1>
  </header>
</template>

<script>
export default {
    name:'headerComponent',
    data(){
        return{
            text_to_search:''
        }
    }
}
</script>

<style scoped lang="scss">
    header{
        height: 15vh;
        background-color: lightblue;
        display: flex;
        justify-content: space-around;
        align-items: center;
        position: fixed;
        right: 0;
        left: 0;
        top: 0;
        z-index: 100;
        
        .search_bar{
            height: 25%;
        }
    }
</style>