<template>
  <header class="d-flex justify-content-between align-items-center">
    <div class="ms-3 text-danger text-uppercase fw-bold fs-2">Boolflix</div>
    <div>
      <form action="" class="me-5">
        <input type="text" v-model="searchText" />
        <button
          type="submit"
          class="btn btn-primary ms-4"
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
</style>
