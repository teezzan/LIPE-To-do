<template>

  <div id="app">
    
    <b-container id="extcon" class="bv-row">
      <h1 id="heading">LIPE To-Do</h1>
    <List      
     />
    </b-container>


    <Footer />
  </div>
</template>

<script>
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    List,
    Footer
  },
  data() {
    return {
      
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#heading {
  margin-top: -35px;
}
</style>
