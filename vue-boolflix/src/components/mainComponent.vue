<template>
  <main>
    <h1>FILM</h1>

    <div class="films">
        <div class="film-card" v-for="film in films " :key="film.id">
        <p>Title: {{film.title}}</p>
        <p>Original title: {{film.original_title}}</p>
        <p>Original language: <img class="flag" :src="getFlag(film.original_language)" :alt="film.original_language"></p>
        <p>Vote: {{film.vote_average}}</p>
    </div>
    </div>

    <h1>SERIE</h1>

    <div class="films">
        <div class="film-card" v-for="tv in series " :key="tv.id">
        <p>Title: {{tv.name}}</p>
        <p>Original title: {{tv.original_name}}</p>
        <p>Original language: <img class="flag" :src="getFlag(tv.original_language)" :alt="tv.original_language"></p>
        <p>Vote: {{tv.vote_average}}</p>
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
    }
}
</script>

<style scoped lang="scss">
    .films{
        display: flex;
        flex-wrap: wrap;
        .film-card{
        border: 1px black solid;
        width: calc(100% / 4);
        display: inline-block;
         .flag{
            width: 20px;
            }
        }
    }
   
  

</style>