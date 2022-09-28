<template>
  <div id="app">
    <headerComponent/>
  </div>
</template>

<script>
  import headerComponent from './components/headerComponent.vue'

  export default {
    name: 'App',
    components: {
      headerComponent,

    },

    data() {
      return{
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=' + 'ciao'
      }
    },

    created(){
      console.log(this.apiUrl)
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
</style>
