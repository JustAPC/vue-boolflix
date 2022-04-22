<template>
  <div>
    <ul>
      <li v-for="(elm, i) in multimediaList" :key="i">
        <ul>
          <li>{{ elm.title }}</li>
          <li>{{ elm.original_title }}</li>
          <li>{{ elm.original_language }}</li>
          <li><img :src="flagFunction(elm.original_language)" /></li>
          <li>{{ elm.vote_average }}</li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "MainComp",
  props: {
    multimediaList: Array,
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
  },
};
</script>

<style scoped lang="scss"></style>
