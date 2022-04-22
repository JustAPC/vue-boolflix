<template>
  <div id="app">
    <HeaderComp @funzioneRicerca="metodoSearch" />
    <div>{{ multimediaList[1].title }}</div>
  </div>
</template>

<script>
import "bootstrap";
import axios from "axios";
import HeaderComp from "./components/HeaderComp.vue";

export default {
  name: "App",
  components: {
    HeaderComp,
  },
  data() {
    return {
      apiKey: "c16fc230072b5fb47643e186e6d0d9ae",
      testoRicerca: "",
      multimediaList: [],
    };
  },

  methods: {
    metodoSearch(testo) {
      this.testoRicerca = testo;
    },

    multimediaFiltering() {
      if (this.testoRicerca === "") {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=ritorno al futuro`
          )
          .then((res) => {
            this.multimediaList = res.data.results;
            console.log(this.multimediaList);
          });
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/discover/movie?api_key=${this.apiKey}&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate`
          )
          .then((res) => {
            this.multimediaList = res.data.results;
            console.log(this.multimediaList);
          });
      }
    },

    created() {
      this.multimediaFiltering();
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
