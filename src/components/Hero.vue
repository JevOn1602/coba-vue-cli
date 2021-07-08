<template>
  <div class="card-hero">
    <img :src="gambar(dataHero.gambar)" :alt="dataHero.nama" />
    <p>{{ ind }} {{ dataHero.nama }}</p>
    <p>Jenis Hero : {{ dataHero.type }}</p>
  </div>
</template>
<script>
export default {
  props: ["dataHero", "ind"],
  data() {
    return {
      hero: [],
    };
  },
  name: "Hero",
  methods: {
    gambar: function(text) {
      return require("../assets/hero/" + text);
    },
  },
};
</script>
// scoped untuk loacl styling
<style scoped>
.card-hero {
  padding: 20px;
  width: min-content;
  height: min-content;
  background-color: white;
  box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.5);
}
</style>
