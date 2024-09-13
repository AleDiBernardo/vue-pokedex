<template>
  <div class="container rounded rounded-5 d-flex p-4">
    <AppSearchPokemon />
    <AppList />
    <img src="../assets/pngegg.png" class="pokeball" alt="" />
  </div>
</template>

<script>
import AppSearchPokemon from "./AppSearchPokemon.vue";
import AppList from "./AppList.vue";

export default {
  data() {
    return {};
  },
  components: {
    AppSearchPokemon,
    AppList,
  },
};
</script>

<style lang="scss" scoped>
.container {
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

  .pokeball {
    // width: 100px;
    // height: 100px;
    background-color: red;
    border: 2px solid black;
    border-radius: 50%;
    animation: shake 3s infinite;
  }

  @keyframes shake {
    0% {
      transform: translateX(0px) rotate(0deg);
      box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5);
    }
    50% {
      transform: translateX(5px) rotate(10deg);
      box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.8);
    }
    100% {
      transform: translateX(0px) rotate(0deg);
      box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5);
    }
  }
}
</style>
