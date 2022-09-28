<template>
  <div id="app">
    <headerComponent @search_this_text="filter_films" />
    <loaderComponent v-if="loading" />

  </div>
</template>

<script>
  import axios from 'axios';
  import loaderComponent from './components/loaderComponent.vue'
  import headerComponent from './components/headerComponent.vue'

  export default {
    name: 'App',
    components: {
      headerComponent,
      loaderComponent
    },

    methods:{
      filter_films(text_to_search){
        this.text_to_search=text_to_search;
        console.log(this.text_to_search);
      }
    },

    data() {
      return{
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=6f73513ffdc9100a85f2ea1e0bc11fd3&query=' + 'ciao',
        loading:true,
        films:[],
        errorMessage:'',
        text_to_search:'',


      }
    },

    created() {
    axios
      .get(this.apiUrl)
      .then(({ status, data }) => {
        this.loading = false;
        if (status === 200) {
          this.films = data.response;
        } else {
          this.errorMessage = 'something went wrong...';
        }
      })
      .catch((error) => {
        console.log(error);
        this.loading = false;
        this.errorMessage = 'error: ' + error.message;
      });
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
