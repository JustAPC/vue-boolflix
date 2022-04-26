<template>
  <div>
    <div v-for="(elm, i) in genreList" :key="i">
      <span>{{ elm.name }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProvaComp",
  props: {
    genreList: Array,
  },
};
</script>

<style scoped lang="scss"></style>
