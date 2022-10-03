<template>
  <div>
    <p v-for="genre in this.genres_movie" :key="genre.id">
        {{genre.name}}
        ciao fra
    </p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name:'genres_movieComponent',

    components:{
        
    },

    data() {
      return{
        loading:false,
        
        genres_movie:[],

        errorMessage:'',
        


      }
    },


    created() {
      axios
        .get('https://api.themoviedb.org/3/genre/movie/list?api_key=6f73513ffdc9100a85f2ea1e0bc11fd3&language=it-IT')
        .then(({ status, data }) => {
          this.loading = false;
          if (status === 200) {
            this.genres_movie = data;
             console.log('generi',this.genres_movie)
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

</style>