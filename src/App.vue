<template>
  <Navbar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer />
</template>

<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';
import './css/global.css';

export default {
  components: {
    Navbar,
    Footer
  },
  data(){
    return{
      logo_src: '/img/logo.png',
      app_name: 'make your burger'
    }
  }
}
</script>


<style>



</style>
