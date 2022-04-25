<template>
  <div class="d-flex p-5 flex-wrap justify-content-start">
    <div v-for="(elm, i) in multimediaList" :key="i">
      <!-- Container multimedia -->
      <div
        class="multimedia-card m-3 mb-5 position-relative"
        @mouseover="hover = true"
        @mouseleave="hover = false"
      >
        <!-- Immagine di copertina -->
        <img
          class="multimedia-poster"
          :src="`https://image.tmdb.org/t/p/w342/${elm.poster_path}`"
          :alt="`immagine di copertina di ${elm.title}`"
          v-if="elm.poster_path != null"
        />
        <img
          src="../assets/unknown.png"
          class="multimedia-poster"
          alt="immagine di copertina indefinita"
          v-else
        />

        <!-- Descrizione multimedia -->
        <div class="multimedia-info text-white p-3" v-if="hover">
          <div><span>Titolo: </span>{{ elm.title }}</div>
          <div v-if="elm.title != elm.original_title">
            <span>Titolo Originale: </span> {{ elm.original_title }}
          </div>
          <div>
            <span>Original Language: </span>
            <img :src="flagFunction(elm.original_language)" />
          </div>
          <div><span>Overview: </span>{{ elm.overview }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainComp",
  props: {
    multimediaList: Array,
  },

  data() {
    return {
      hover: false,
    };
  },

  methods: {
    flagFunction(index) {
      if (index == "en") {
        index = "https://flagcdn.com/w20/gb.png";
        return index;
      } else if (index == "it") {
        index = "https://flagcdn.com/w20/it.png";
        return index;
      } else if (index == "de") {
        index = "https://flagcdn.com/w20/de.png";
        return index;
      } else if (index == "fr") {
        index = "https://flagcdn.com/w20/fr.png";
        return index;
      } else if (index == "es") {
        index = "https://flagcdn.com/w20/es.png";
        return index;
      } else {
        index = "https://flagcdn.com/w20/aq.png";
        return index;
      }
    },

    getNewRating(index) {
      index = Math.round(index / 2);
      return index;
    },
  },
};
</script>

<style scoped lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

ul li {
  list-style-type: none;
}

.multimedia-card {
  height: 510px;
  width: 342px;
  cursor: pointer;
}

.multimedia-card:hover {
  background-image: url();
  background-color: black;
}

.multimedia-poster {
  height: 510px;
  width: 342px;
}

.multimedia-info {
  background-color: black;
  display: block;
  position: absolute;
  top: 0;
  left: 0%;
  text-align: start;
  height: 510px;
  width: 342px;
  overflow-y: scroll;
}

.multimedia-info::-webkit-scrollbar {
  display: none;
}

span {
  font-weight: bold;
}
</style>
