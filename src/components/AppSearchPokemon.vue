<template>
  <div class="left w-100 h-100 d-flex flex-column align-items-center">
    <header
      class="searchHeader d-flex align-items-center justify-content-between w-100"
    >
      <input
        type="search"
        name="searchbar"
        placeholder="Search a Pokémon"
        autocomplete="off"
        id="query"
        class="p-1 rounded rounded-3"
        v-model="this.store.userQuery"
        @keyup.enter="search"
      />
      <button class="btn btn-light">Catch it!</button>
    </header>
    <main class="d-flex flex-column gap-3 h-100">
      <div
        class="d-flex justify-content-center align-items-center mt-3 p-3 text-bg-secondary rounded rounded-3"
      >
        <div
          class="display bg-light border border-5 border-black rounded rounded-3"
        >
          <img src="" alt="" />
        </div>
      </div>
      <div class="stats w-100 h-100 rounded rounded-3 p-4">
        <div v-if="this.store.results" class="d-flex flex-column">
          <ul class="p-0">
            <li>
              <span class="fw-bold"> Name:</span> {{ this.store.results.name }}
            </li>
            <li>
              <span class="fw-bold"> Type:</span> {{ this.store.results.types[0].type.name }}
            </li>
            <li>
              <span class="fw-bold"> Height:</span> {{ this.store.results.height + '"' }}
            </li>
            <li>
              <span class="fw-bold"> Weight:</span> {{ this.store.results.weight + " lbs" }}
            </li>
          </ul>
          <div>

            <span class="fw-bold">Stats</span>
            <ul class="p-0">
              <li v-for="curStat in this.store.results.stats ">
                  {{ curStat.stat.name + ": " + curStat.base_stat }}
              </li>
            </ul>
          </div>
        </div>
        <span v-else>Search a Pokémon</span>

        <!-- {{ this.store.results ? this.store.results.name : "No results" }} -->
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {
    search() {
      axios
        .get(`https://pokeapi.co/api/v2/pokemon/${this.store.userQuery}/`)
        .then((resp) => {
          this.store.results = resp.data;
          console.log(this.store.results);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
.left {
  // border-right:  5px solid rgb(156, 0, 0);

  main {
    // margin-right: 10px;
    width: 90%;
    .display {
      width: 90%;
      height: 300px;
    }

    .stats {
      background: greenyellow;

      ul{
        li{
          list-style-type: none;
        }
      }
    }
  }
}
</style>
