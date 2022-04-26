<template>
  <div class="d-flex p-3 flex-wrap justify-content-start">
    <div v-for="(elm, i) in multimediaList" :key="i">
      <!-- Container multimedia -->
      <div
        class="multimedia-card m-3 mb-5 position-relative"
        @mouseover="mouseOver(i)"
        @mouseleave="hover = false"
      >
        <div class="flip-card">
          <div class="flip-card-inner">
            <div class="flip-card-front">
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
            </div>

            <div class="flip-card-back">
              <div class="multimedia-info text-white p-3" v-show="hover && i === mouseOverIndex">
                <!-- Titolo -->
                <div><span>Titolo: </span>{{ elm.title }}</div>
                <div v-if="elm.title != elm.original_title">
                  <span>Titolo Originale: </span> {{ elm.original_title }}
                </div>
                <!-- Lingua -->
                <div>
                  <span>Original Language: </span>
                  <img :src="flagFunction(elm.original_language)" />
                </div>
                <!-- Voto -->
                <div v-if="getNewRating(elm.vote_average) != 0">
                  <div class="d-inline-block">
                    <span>Voto: </span>
                    <span v-for="(elm, i) in getNewRating(elm.vote_average)" :key="i">
                      <i class="fa-solid fa-star active-stars"></i>
                    </span>
                  </div>

                  <div class="d-inline-block">
                    <span v-for="(elm, i) in 5 - getNewRating(elm.vote_average)" :key="i">
                      <i class="fa-solid fa-star empty-stars"></i>
                    </span>
                  </div>
                </div>

                <div v-else><span>Not voted yet!</span></div>

                <!-- Overview -->
                <div><span>Overview: </span>{{ elm.overview }}</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Descrizione multimedia -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainComp",
  props: {
    multimediaList: Array,
    genreList: Array,
  },

  data() {
    return {
      hover: false,
      mouseOverIndex: null,
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

    mouseOver(index) {
      this.hover = true;
      this.mouseOverIndex = index;
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
  perspective: 1000px;
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

.empty-stars {
  color: grey;
}

.active-stars {
  color: yellow;
}

.multimedia-info div {
  padding: 5px 0;
}

span {
  font-weight: bold;
}

.flip-card {
  background-color: transparent;
  height: 100%;
  width: 100%;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: transparent;
}

.flip-card-back {
  background-color: transparent;
  transform: rotateY(180deg);
}
</style>
