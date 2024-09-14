<template>
  <div class="right p-4 w-100 h-100">
    <div class="list w-100 h-100 rounded rounded-3 bg-body p-4">
      <h4>My Pokémons</h4>
      <span class="text-dark" v-if="this.store.catchedPokemon.length > 0">
        <ul class="p-0">
          <li
            v-for="curPokemon in this.store.catchedPokemon"
            :key="curPokemon.id"
            @click="selectPokémon(curPokemon)"
            
          >
            {{ curPokemon.name.charAt(0).toUpperCase() + curPokemon.name.slice(1)}}
          </li>
        </ul>
      </span>
    </div>
  </div>
</template>

<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  mounted(){
    if(localStorage.getItem('catchedPokemon')){
      this.store.catchedPokemon = JSON.parse(localStorage.getItem('catchedPokemon'));
      console.log("Dati presi: " + this.store.catchedPokemon);
      
    }
  },
  methods:{
    selectPokémon(curPokemon){
      this.store.results = curPokemon;
    }
  }
};
</script>

<style lang="scss" scoped>
  li{
    cursor: pointer;
    &:hover{
      font-weight: bold;
    }
  }
</style>
