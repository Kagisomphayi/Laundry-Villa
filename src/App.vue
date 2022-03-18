<template>
  <div id="nav">
     <SocialNav/>
     <Navbar />
  </div>
  <router-view/>
  <Footer />

</template>

<script>
import Navbar from './components/Navbar'
import SocialNav from './components/SocialNav'
import Footer from './components/Footer'
export default {
  components:{
    Navbar,SocialNav,Footer
  },
  
}
</script>

<style>
#nav a {
  font-weight: bold;
  color: rgba(10, 81, 139, 0.979);
}

#nav a.router-link-exact-active {
  color: rgba(139, 102, 96, 0.924);
}
</style>
