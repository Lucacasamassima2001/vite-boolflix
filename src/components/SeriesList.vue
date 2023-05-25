<script>
import { store } from '../store';


export default {
data(){
    return{
        store,
    }
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
            <div>{{ serie.original_language }} </div>
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