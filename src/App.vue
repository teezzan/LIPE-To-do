<template>
  <div id="app">
    <Header />
    <b-container id="extcon" class="bv-example-row">
    <List
      
     />
    </b-container>


    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    List,
    Footer
  },
  data() {
    return {
      tasks: [
        {"todo":"Hello Lorem","done":false},
        {"todo":"Ipsium Lorem","done":false},
        {"todo":"Saola code","done":true}
        ],
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
</style>
