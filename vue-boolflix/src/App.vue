<template>
  <div id="app">
    <headerComponent @search_this_text="filter_films" />
    <loaderComponent v-if="loading" />
    <mainComponent :films="films" />
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
        this.loading=true;
           
        axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=6f73513ffdc9100a85f2ea1e0bc11fd3&query=${text_to_search}&language=it-IT`)
        .then(({ status, data }) => {
          this.loading = false;
          if (status === 200) {
            this.films = data.results;
            // console.log(this.films.results.title)
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
        loading:false,
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
