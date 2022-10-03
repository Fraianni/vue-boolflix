<template>
  <main>
    <h1>FILM</h1>

    <div class="films">
        <div class="film-card" v-for="film in films " :key="film.id">
        <p>Title: {{film.title}}</p>
        <p>Original title: {{film.original_title}}</p>
        <p>Original language: <img class="flag" :src="getFlag(film.original_language)" :alt="film.original_language"></p>
        <p>Vote:
            <span v-for="counter in 5" :key="counter">
                <font-awesome-icon v-if="counter <= voteToStars(film.vote_average) " icon="fa-solid fa-star" />
                <font-awesome-icon v-else icon="fa-regular fa-star" />

            </span>
        </p>
        <img :src="getPoster(film.poster_path)" alt="">
    </div>
    </div>

    <h1>SERIE</h1>

    <div class="films">
        <div class="film-card" v-for="tv in series " :key="tv.id">
        <p>Title: {{tv.name}}</p>
        <p>Original title: {{tv.original_name}}</p>
        <p>Original language: <img class="flag" :src="getFlag(tv.original_language)" :alt="tv.original_language"></p>
        <p>Vote: 
            <span v-for="counter in 5" :key="counter">
                <font-awesome-icon v-if="counter <= voteToStars(tv.vote_average) " icon="fa-solid fa-star" />
                <font-awesome-icon v-else icon="fa-regular fa-star" />

            </span>
        </p>
        <img :src="getPoster(tv.poster_path)" alt="">

    </div>
    </div>

  </main>
</template>

<script>
export default {
    name:'mainComponent',

    props:{
        films:Array,
        series:Array
    },

    methods:{
        getFlag(country){
                if(country==='en'){
                    country='gb';
                }
                else if(country==='ja'){
                    country='jp';
                }

            return `https://flagicons.lipis.dev/flags/1x1/${country}.svg`
            
        },

        getPoster(poster_path){
            return `http://image.tmdb.org/t/p/w185/${poster_path}`
        },

        voteToStars(vote_average){
            const star_number = Math.ceil(vote_average/2);
            console.log(vote_average,star_number);
            if(star_number===0)
                return 'n/d';
            return star_number;
        }
    }
}
</script>

<style scoped lang="scss">
    main{
        h1{
             text-align: center;

        }

        .films{
        display: flex;
        flex-wrap: wrap;
        .film-card{
            border: 1px black solid;
            width: calc(100% / 4);
            display: inline-block;
            background-color:lightblue;
            color: white;
        
            .flag{
                width: 20px;
            }
        }
    }
    }
 
   
  

</style>