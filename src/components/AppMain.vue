
<script>
import {store} from '../store';
import FilmList from './FilmList.vue';
import AppHeader from './AppHeader.vue';

export default {
    data(){
        return{
            store,
        }
    },

    components:{
        FilmList,
    }

}
</script>


<template>
    <FilmList/>
</template>

<style>

</style>