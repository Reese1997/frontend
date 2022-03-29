<template>
<Navbar/>
   <router-view/>
</template>

<script>


import Navbar from '../src/components/Navbar.vue'
export default {
  
  name: "App",
  components: { Navbar
  }
}
</script>

<style scoped>
#app {
 font-family: 'Bebas Neue', cursive;
font-family: 'League Gothic', sans-serif;
font-family: 'Smooch Sans', sans-serif;  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
