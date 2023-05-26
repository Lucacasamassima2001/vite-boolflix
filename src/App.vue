<script>
import {store} from './store';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


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
            include_adult: false,
            language: "it-IT",
            query: this.store.Searchtext,
          },
          headers: {
            accept: "application/json",
          },
        })
        .then((response) => (this.store.FilmList = response.data.results));

        axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: this.store.ApiKey,
            include_adult: false,
            language: "it-IT",
            query: this.store.Searchtext,
          },
          headers: {
            accept: "application/json",
          },
        })
        .then((response) => (this.store.SeriesList = response.data.results));
    },
  },

  

}
</script>


<template>
  <div class="container">
    <AppHeader @performsearch="RequestFilms"/>
    <AppMain/>
  </div>
  

</template>


<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}




</style>




<!-- TO DO FLAGS -->