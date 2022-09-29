<template>
  <main>
    <div class="film-card" v-for="film in films " :key="film.id">
        <p>Title: {{film.title}}</p>
        <p>Original title: {{film.original_title}}</p>
        <p>Original language: <img class="flag" :src="getFlag(film.original_language)" :alt="film.original_language"></p>
        <p>Vote: {{film.vote_average}}</p>
    </div>
  </main>
</template>

<script>
export default {
    name:'mainComponent',

    props:{
        films:Array,
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
    .film-card{
        border: 1px black solid;
        .flag{
        width: 20px;
    }
    }
  

</style>