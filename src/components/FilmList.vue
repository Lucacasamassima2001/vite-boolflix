<script>
import { store } from '../store';


export default {
data(){
    return{
        store,
    }
},




}
</script>


<template>
  <div class="card" v-for="film in store.FilmList" :key="film.id">
    <div>{{ film.title }} </div>
    <div>{{ film.original_title }} </div>
    <div>{{ film.original_language }} </div>
    <div>{{ film.vote_average }} </div>
  </div>

</template>



<style  scoped>

    .card{
        border: 2px solid black;
    }

    div{
        margin-top: 1em;
    }
</style>