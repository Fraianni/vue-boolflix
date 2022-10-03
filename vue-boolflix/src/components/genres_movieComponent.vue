<template>
  <div class="genres">
    <p v-for="genre in this.genres_movie" :key="genre.id">
        {{genre.name}}
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

    props:{
        films:Array
    },


    created() {
      axios
        .get('https://api.themoviedb.org/3/genre/movie/list?api_key=6f73513ffdc9100a85f2ea1e0bc11fd3&language=it-IT')
        .then(({ status, data }) => {
          this.loading = false;
          if (status === 200) {
            this.genres_movie = data.genres;
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

<style scoped lang="scss">
    .genres{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        >*{
            margin: 10px;
        }
    }

</style>