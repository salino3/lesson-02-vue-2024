<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Home :title="getTitle" />
</template>

<script>
import Home from './components/home-page.vue';
import {apiCall} from './apis/get-info';

export default {
  name: 'App',
  components: {
    Home
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
     getNameTitle() {
     return this.pageTitle = this.characters[2].name
    }
  },
  async created() {
    try {
      this.characters = await apiCall();
      console.log(this.characters);
      this.getNameTitle();
    } catch (error) {
      console.error("Error in the API call:", error);
    }
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
}
</style>
