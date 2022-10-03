<template>
  <main>
    <h1>FILM</h1>

    <div class="films">

        <genres_movieComponent :films="films"  />


        <div class="card" v-for="film in films " :key="film.id">
             <div class="img-card">
                <img :src="getPoster(film.poster_path)" alt="">
            </div>
          
            <div class="info-card">
                <p>Title: {{film.title}}</p>
                <p>Original title: {{film.original_title}}</p>
                <p>Original language: <img class="flag" :src="getFlag(film.original_language)" :alt="film.original_language"></p>
                <p>Vote:
                    <span v-for="counter in 5" :key="counter">
                        <font-awesome-icon v-if="counter <= voteToStars(film.vote_average) " icon="fa-solid fa-star" />
                        <font-awesome-icon v-else icon="fa-regular fa-star" />

                    </span>
                </p>
                <p class="overview">Overview: {{film.overview}}</p>
            </div>
            
           
        </div>

        
    </div>

    <h1>SERIE</h1>


    <div class="films">
        <div class="card" v-for="tv in series " :key="tv.id">
             <div class="img-card">
                <img :src="getPoster(tv.poster_path)" alt="">
            </div>
          
            <div class="info-card">
                <p>Title: {{tv.name}}</p>
                <p>Original title: {{tv.original_name}}</p>
                <p>Original language: <img class="flag" :src="getFlag(tv.original_language)" :alt="tv.original_language"></p>
                <p>Vote:
                    <span v-for="counter in 5" :key="counter">
                        <font-awesome-icon v-if="counter <= voteToStars(tv.vote_average) " icon="fa-solid fa-star" />
                        <font-awesome-icon v-else icon="fa-regular fa-star" />

                    </span>
                </p>
                <p class="overview">Overview: {{tv.overview}}</p>

            </div>
            
           
        </div>

        
    </div>

  </main>
</template>

<script>

    import genres_movieComponent from './genres_movieComponent.vue';

    export default {
        name:'mainComponent',

        components: {
            genres_movieComponent,
        },

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
                return `http://image.tmdb.org/t/p/w342/${poster_path}`
            },

            voteToStars(vote_average){
                const star_number = Math.ceil(vote_average/2);
                if(star_number===0)
                    return 'n/d';
                return star_number;
            }
        }
    }
</script>

<style scoped lang="scss">
    main{
        padding-top: 150px;

        h1{
             text-align: center;

        }

        .films{
            display: flex;
            flex-wrap: wrap;
            .card{
                margin: 10px;
                width: calc(100% / 5);
                display: inline-block;
                background-color:black;
                color: white;
                position: relative;
                height:400px;
                
        
                .flag{
                    width: 20px;
                }
                
                .info-card{
                    width: 100%;
                    font-size: 0.8rem;
                }

                .img-card{
                    width: 100%;

                    position: absolute;
                    top: 0;
                    left: 0;

                    img{
                        height: 400px;
                        width: 100%;
                    }
                    
                }
            }

            .img-card:hover{
                opacity: 0.1;
            }

        }
        
        .overview{
                max-height: 100px;
                font-size: 0.6rem;
            }
    }
 
   
  

</style>