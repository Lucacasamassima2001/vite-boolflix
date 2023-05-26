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
    
}


}
</script>



<template>
    <h1 v-show="store.SeriesList!=0">TV Shows:</h1>
    <div class="container">
        <div class="card" v-for="serie in store.SeriesList" :key="serie.id">
            <div class="card-inner">
                <div class="card-front">
                    <img :src="'https://image.tmdb.org/t/p/w342'+serie.poster_path" onerror="this.style.display='none'">
                    <img v-if="serie.poster_path == null" src="../assets/img/No-Photo-Available.webp" :alt="serie.title" >
                </div>
                <div class="card-back">
                    <div>{{ serie.name }} </div>
            <div>{{ serie.original_name }} </div>

            <!-- PER SISTEMARE LE FLAG MANCANTI SI POTREBBE ANCHE INTERVENIRE SULLO STILE flag-undefined -->
            <country-flag  v-if="serie.original_language=== 'en'" country="gb" size='normal'/>
            <country-flag  v-else-if="serie.original_language=== 'ko'" country="kr" size='normal'/>
            <country-flag  v-else-if="serie.original_language=== 'ja'" country="jp" size='normal'/>
            <country-flag  v-else-if="serie.original_language=== 'zh'" country="ch" size='normal'/>
            <country-flag  v-else-if="serie.original_language=== 'hi'" country="in" size='normal'/>
            <country-flag  v-else :country="serie.original_language" size='normal'/>
            <div class="stars">
                <span v-for="star in Math.ceil(serie.vote_average / 2)" :key="star"> 
                    <font-awesome-icon :icon="['fas', 'star']" style="color: #FFBF00;" />
                </span>
                <span v-for="star in Math.floor(5 - serie.vote_average / 2)" :key="star"> 
                    <font-awesome-icon :icon="['fas', 'star']" style="color: grey;" />
                </span>
            </div>
            <div class="overview">"{{ serie.overview }}"</div>
                </div>
            </div>
        </div>
    </div>
  

</template>



<style lang="scss"  scoped>
@use '../assets/style/partials/variables.scss'as *;


.container{
    @include container
}

.card{
        @include card-settings;
        perspective: 1000px;
    }

    .card-inner{
        @include card-inner;
    }

    .card:hover .card-inner {
    transform: rotateY(180deg);
}

.card-front, .card-back{
    @include card-front-back;
}

.card-front{
    color: black;
}

.card-back{
    background-color: #1f1f20;
    color: white;
    transform: rotateY(180deg);
    padding: 1em;
}

h1{
    text-align: center;
    margin-top: 2em;
    color: white;
}

    .card{
        @include card-settings;
        
    }

    .overview{
    font-style: italic;
    line-height: 1.2em;
}

    img{
        width: 100%;
        height: 550px;
    }

    div{
        margin-top: 1em;
    }
</style>