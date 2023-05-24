
<script>
import {store} from '../store';

export default {

    data(){
        return{
            store,
        }
    },



    methods:{
        emitsearchevent() {
        this.$emit("performsearch");
    },
    }
}
</script>


<template>
  <div>
    <h1>Boolflix</h1>
    <input type="text" v-model="store.Searchtext" id="one" >
    <button @click="emitsearchevent">Search</button>
  </div>
</template>

<style>

</style>