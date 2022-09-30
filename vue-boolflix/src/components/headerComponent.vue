<template>
  <header>
    <input v-model="text_to_search" type="text" placeholder="Cerca film" @keyup.enter="$emit('search_this_text', text_to_search)">
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

<style scoped>
    header{
        height: 15vh;
        background-color: lightblue;
    }
</style>