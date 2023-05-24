<script>
import {store} from './store';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
// import FilmList from './components/FilmList.vue';
// import SeriesList from './components/SeriesList.vue';

export default {
  data(){
    return{
      store,

    };
  },

  components:{
    AppHeader,
    AppMain,
    // FilmList,
    // SeriesList,
  },

  


  methods: {
    RequestFilms() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: this.store.ApiKey,
            include_adult: true,
            language: "it-IT",
            query: this.store.Searchtext,
          },
          headers: {
            accept: "application/json",
          },
        })
        .then((response) => (this.store.FilmList = response.data.results));
    }
    
  },

  // created(){
    // axios.get('https://api.themoviedb.org/3/search/movie?query=https%253A%252F%252Fapi.themoviedb.org%252F3%252Fsearch%252Fmovie&include_adult=false&language=it-IT&page=1&api_key=7f8fb90e175b01e2da4d64c393b86259&query=all')
    // .then(response => (this.store.FilmList = response.data.results));
  // }

}
</script>


<template>
  <AppHeader @performsearch="RequestFilms" />
  <AppMain/>

</template>


<style>

</style>