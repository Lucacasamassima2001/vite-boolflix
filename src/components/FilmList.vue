<script>
import { store } from '../store';
import CountryFlag from "vue-country-flag-next";
import LangFlag from 'vue-lang-code-flags';



export default {
data(){
    return{
        store,
        
    }
},


components:{
    CountryFlag,
    // LangFlag,
},

methods:{
    
},


}
</script>


<template>
    <h1 v-show="store.FilmList!=0">Movies:</h1>
    <div class="container">
        <div class="card" v-for="film in store.FilmList" :key="film.id">
            <img :src="'https://image.tmdb.org/t/p/w342'+film.poster_path" :alt="film.title" >
            <div>{{ film.title }} </div>
            <div>{{ film.original_title }} </div>
            <country-flag  v-if="film.original_language=== 'en'" country="gb" size='normal'/>
            <country-flag  v-else-if="film.original_language=== 'ko'" country="kr" size='normal'/>
            <country-flag  v-else-if="film.original_language=== 'ja'" country="jp" size='normal'/>
            <country-flag  v-else-if="film.original_language=== 'zh'" country="ch" size='normal'/>
            <country-flag  v-else-if="film.original_language=== 'hi'" country="in" size='normal'/>
            <country-flag  v-else :country="film.original_language" size='normal'/>
            <div class="stars">
                <span v-for="star in Math.ceil(film.vote_average / 2)" :key="star"> 
                    <font-awesome-icon :icon="['fas', 'star']" style="color: #FFBF00;" />
                </span>
                <span v-for="star in Math.floor(5 - film.vote_average / 2)" :key="star"> 
                    <font-awesome-icon :icon="['fas', 'star']" style="color: grey;" />
                </span>
            </div>
            
        </div>
    </div>
  

</template>



<style  scoped>


.container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1em;
}

h1{
    text-align: center;
    margin-top: 2em;
    color: white;

}

    .card{
        margin-top: 5em;
        text-align: center;
        width: 342px;
        height: 700px;
        border: 2px solid black;
    }

    img{
        width: 100%;
    }

    div{
        margin-top: 1em;
    }

    span{
        margin-left: .5em;
    }
</style>