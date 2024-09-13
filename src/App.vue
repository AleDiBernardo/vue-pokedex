<template>
  <div class="container d-flex justify-content-center align-items-center h-100 w-100">
    <AppPokedex/>
  </div>
</template>

<script>
import AppPokedex from "./components/AppPokedex.vue";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap.bundle.min.js";
export default {
  data(){
    return{
      
    }
  },
  components: {
    AppPokedex
  }
}
</script>

<style lang="scss">
  body{
    height: 100vh;
    background: url('./assets/erba.jpeg');
    background-repeat: no-repeat;
    background-size: cover;

    #app {
      height: 100%;
    }
  }
</style>