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
    DefaultImg(){
        if(film.poster_path === null){
            return '../assets/img/placeholder.jpg'
        }
        
    }
},


}
</script>


<template>
    <h1 v-show="store.FilmList!=0">Movies:</h1>
    <div class="container">
        <div class="card" v-for="film in store.FilmList" :key="film.id">
            <div class="card-inner">
                <div class="card-front">
                    <img  :src="'https://image.tmdb.org/t/p/w342'+film.poster_path" :alt="film.title" onerror="this.style.display='none'">
                    <img v-if="film.poster_path == null" src="../assets/img/No-Photo-Available.webp" :alt="film.title" >
                </div>
                <div class="card-back">
                    <div>Titolo: {{ film.title }} </div>
                    <div>Titolo Originale: {{ film.original_title }} </div>
                    <span>Paese d'origine: </span>
                    <country-flag  v-if="film.original_language=== 'en'" country="gb" size='normal'/>
                    <country-flag  v-else-if="film.original_language=== 'ko'" country="kr" size='normal'/>
                    <country-flag  v-else-if="film.original_language=== 'ja'" country="jp" size='normal'/>
                    <country-flag  v-else-if="film.original_language=== 'zh'" country="ch" size='normal'/>
                    <country-flag  v-else-if="film.original_language=== 'hi'" country="in" size='normal'/>
                    <country-flag  v-else :country="film.original_language" size='normal'/>
                    <div class="stars">
                    <span>Voto: </span>
                    <span v-for="star in Math.ceil(film.vote_average / 2)" :key="star"> 
                        <font-awesome-icon :icon="['fas', 'star']" style="color: #FFBF00;" />
                    </span>
                    <span v-for="star in Math.floor(5 - film.vote_average / 2)" :key="star"> 
                        <font-awesome-icon :icon="['fas', 'star']" style="color: grey;" />
                    </span>
                </div>
                <div class="overview">"{{ film.overview }}"</div>
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

h1{
    text-align: center;
    margin-top: 2em;
    color: white;

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
    overflow: auto;

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

    span{
        margin-left: .5em;
    }
</style>