<template>
  <div id="app">
    <headerComponent @search_this_text="filter_films" />
    <loaderComponent v-if="loading" />
    <mainComponent v-else />

  </div>
</template>

<script>
  import axios from 'axios';
  import loaderComponent from './components/loaderComponent.vue'
  import headerComponent from './components/headerComponent.vue'
  import mainComponent from './components/mainComponent.vue'

  export default {
    name: 'App',
    components: {
      loaderComponent,
      headerComponent,
      mainComponent,

    },

    methods:{
      filter_films(text_to_search){
      
        console.log(text_to_search);
           
        axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=6f73513ffdc9100a85f2ea1e0bc11fd3&query= ${text_to_search}`)
        .then(({ status, data }) => {
          this.loading = false;
          if (status === 200) {
            this.films = data.results;
            console.log(data.results)
          } else {
            this.errorMessage = 'something went wrong...';
          }
        })
        .catch((error) => {
          console.log(error);
          this.loading = false;
          this.errorMessage = 'error: ' + error.message;
        });

      }
    },

    data() {
      return{
        apiUrl: '',
        loading:true,
        films:[],
        errorMessage:'',
        text_to_search:'',
        


      }
    },

    mounted() {
   
    },
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
</style>
