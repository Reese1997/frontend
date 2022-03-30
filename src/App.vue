<template>
<Navbar/>
   <router-view/>
   <Footer/>
</template>

<script>
import Navbar from '../src/components/Navbar.vue'
import Footer from '../src/components/Footer.vue'

export default {
  
  name: "App",
  components: { Navbar,
  Footer
  }
}
</script>

<style scoped>
#app {
 font-family: 'Bebas Neue', cursive;
font-family: 'League Gothic', sans-serif;
font-family: 'Roboto', sans-serif;
font-family: 'Smooch Sans', sans-serif;
  text-align: center;
}
</style>
