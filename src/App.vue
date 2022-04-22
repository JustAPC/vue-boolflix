<template>
  <div id="app">
    <HeaderComp @funzioneRicerca="metodoSearch" />
    <MainComp :multimediaList="multimediaList" />
  </div>
</template>

<script>
import "bootstrap";
import axios from "axios";
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },

  data() {
    return {
      apiKey: "c16fc230072b5fb47643e186e6d0d9ae",
      multimediaList: [],
      testoRicerca: "",
    };
  },

  created() {
    axios
      .get(
        `https://api.themoviedb.org/3/discover/movie?api_key=${this.apiKey}&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate`
      )
      .then((res) => {
        this.multimediaList == res.data.results;
      });
  },

  methods: {
    metodoSearch(multimediaName) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/multi?api_key=${this.apiKey}&query=${multimediaName}`
        )
        .then((res) => {
          this.multimediaList = res.data.results;
          console.log(this.multimediaList);
        });
    },
  },
};
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
