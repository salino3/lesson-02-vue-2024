<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Home :title="getTitle()" />
  <List :characters="this.characters" />
</template>

<script>
import {apiCall} from './apis/get-info';
import Home from './components/home-page.vue';
import List from './components/list-characters.vue'

export default {
  name: 'App',
  components: {
    Home,
    List
  },
  data() {
    return {
      pageTitle: "Title from getTitle function",
      arrayCharacters: []
    }
  },
    methods: {
    getTitle() {
      return this.pageTitle;
    },

     async getNameTitle() {
      try {
        this.characters = await apiCall();
        console.log(this.characters);
        this.pageTitle = this.characters[2].name;
      } catch (error) {
        console.error("Error in the API call:", error);
      }
    }
  },
   async created() {
    this.getNameTitle(); 
  },
  // mounted() executes before created()
  mounted() {
  console.log("message from mounted")
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
