<template>
  <div id="nav">
    <Navbar />
    <router-view />
    <Footer/>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Karla&display=swap");
#app {
  font-family: "Karla", sans-serif;
  height: 100vh;
  background-color: #184d47;
}
</style>

<script>
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";
export default {
  data() {
    return {};
  },

  components: {
    Navbar,
    Footer
},
};
</script>
