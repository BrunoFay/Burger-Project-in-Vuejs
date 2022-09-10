<script setup>
  import {RouterView } from 'vue-router'
</script>
<script>
  import Navbar from './components/Navbar.vue';
  import CFooter from './components/Footer.vue';

  export default {
    components:{
      Navbar,
      CFooter,
    }
  }

</script>

<template>
  <Navbar/>
  <RouterView />
  <CFooter/>

</template>

<style>
*{
  margin: 0;
  padding: 0;
  text-decoration: none;
  box-sizing: border-box;
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
  font-family: 'Roboto', 'Helvetica',sans-serif;
  overflow-x: hidden;
}


</style>
