<template>
  <div class="container rounded rounded-5 d-flex p-4">
    <AppSearchPokemon/>
    <AppList/>
    <img src="../assets/pngegg.png" alt="">
  </div>
</template>

<script>
import AppSearchPokemon from './AppSearchPokemon.vue'
import AppList from './AppList.vue'


export default {
    data(){
        return {

        }
    },
    components: {
        AppSearchPokemon,
        AppList
    }
}
</script>

<style lang="scss" scoped>
.container{
    width: 1000px;
    height: 800px;
    background: red;
    border: 10px solid rgb(156, 0, 0);
    position: relative;
    
    img {
        position: absolute;
        bottom: -50px;
        right: -50px;
    }
}
</style>