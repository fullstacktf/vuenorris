<template>
  <div>
    <NorrisJoke type="nicolas" />
    <NorrisJoke type="chuck" />
  </div>
</template>

<script>
import NorrisJoke from "./components/NorrisJoke.vue";

export default {
  name: "App",
  components: {
    NorrisJoke
  },
  data() {
    return {};
  }
};
</script>

<style></style>
