
<script>
import {store} from '../store';

export default {

    data(){
        return{
            store,
        }
    },



    methods:{
        emitsearcheventfilms() {
        this.$emit("performsearch");
    },
    
    }
}
</script>


<template>
  <div class="container">
    <div>
        <h1>Boolflix</h1>
    </div>
    <div class="container-search">
        <input @keyup.enter="emitsearcheventfilms" type="text" v-model="store.Searchtext" id="SearchBar" placeholder="Cerca...">
        <button @click="emitsearcheventfilms">Cerca</button>
    </div>
  </div>
</template>

<style scoped>
h1{
    font-size: 4em;
}

.container{
    color: red;
    background-color: rgb(30, 29, 29);
    padding: 2em;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.container-search{
    display: flex;
    justify-content: flex-end;
}


button{
    padding: .8em;
    font-size: 1.3em;
    background-color: black;
    border: 2px solid red;
    color: red;
    
}

input{
    width: 300px;
    font-size: 1.3em;
    padding-inline-start: .7em;
    border: 2px solid red;
    color: white;
    background-color: black;
}

</style>