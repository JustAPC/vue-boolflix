<template>
  <div>
    <ul>
      <li v-for="(elm, i) in multimediaList" :key="i">
        <ul>
          <li>{{ elm.original_title }}</li>
          <li>{{ elm.title }}</li>
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
        index = "https://flagcdn.com/w160/gb.png";
        console.log(index);
      }
    },
  },
};
</script>

<style scoped lang="scss"></style>
