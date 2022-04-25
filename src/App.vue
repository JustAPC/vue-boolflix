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
    this.getHomeMultimedia();
  },

  methods: {
    // metodoSearch(multimediaName) {
    //   let apiQuery = multimediaName.replace(/ /g, "%20");
    //   axios
    //     .get(`https://api.themoviedb.org/3/search/multi?api_key=${this.apiKey}&query=${apiQuery}`)
    //     .then((res) => {
    //       this.multimediaList = res.data.results;
    //       console.log(this.multimediaList);
    //     });
    // },

    metodoSearch(multimediaName) {
      this.multimediaList = [];
      let apiQuery = multimediaName.replace(/ /g, "%20");
      axios
        .all([
          axios.get(
            `https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${apiQuery}`
          ),
          axios.get(
            `https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${apiQuery}`
          ),
        ])
        .then(
          axios.spread((moviesRes, tvseriesRes) => {
            this.multimediaList.push(...moviesRes.data.results);
            this.multimediaList.push(...tvseriesRes.data.results);
          })
        );
      console.log(this.multimediaList);
      return this.multimediaList;
    },

    getHomeMultimedia() {
      axios
        .get(`https://api.themoviedb.org/3/trending/movie/week?api_key=${this.apiKey}`)
        .then((res) => {
          this.multimediaList = res.data.results;
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

body {
  background-color: rgb(87, 87, 87);
}
</style>
