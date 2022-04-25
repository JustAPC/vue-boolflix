<template>
  <header class="d-flex justify-content-between align-items-center">
    <div class="ms-3"><a href="#" class="text-danger text-uppercase fw-bold fs-2">Boolflix</a></div>
    <div>
      <form action="" class="me-5">
        <input type="text" v-model="searchText" class="py-1" />
        <button
          type="submit"
          class="btn btn-danger ms-4"
          @click.prevent="$emit('funzioneRicerca', searchText)"
        >
          Ricerca
        </button>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  props: {},
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  background-color: black;
  height: 100px;
}

a {
  text-decoration: none;
}
</style>
