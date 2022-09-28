<template>
  <header>
    <input v-model="text_to_search" type="text" placeholder="Cerca film">
  </header>
</template>

<script>
export default {
    name:'headerComponent'
}
</script>

<style scoped>
    header{
        height: 15vh;
        background-color: red;
    }
</style>