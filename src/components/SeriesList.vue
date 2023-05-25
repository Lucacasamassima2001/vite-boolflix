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
            <img :src="'https://image.tmdb.org/t/p/w342'+serie.poster_path">
            <div>{{ serie.name }} </div>
            <div>{{ serie.original_name }} </div>
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
        </div>
    </div>
  

</template>



<style  scoped>


.container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1em;
    margin-bottom: 2em;
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
</style>