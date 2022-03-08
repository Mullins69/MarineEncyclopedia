<template>
  <Navbar/>
  
  <router-view/>

</template>

<script>

import Navbar from "./components/Navbar.vue"
export default {
  components: {
    Navbar,

  }
}

</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans&display=swap');
body{
  font-family: 'Open Sans', sans-serif !important; 
}
</style>
