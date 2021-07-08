<template>
  <Header @ganti-hero="gantiHero">
    <template v-slot:heroRand>
      <HeroShow :dataHero="hero[current]"></HeroShow>
    </template>
  </Header>
  <main>
    <h2>Daftar Hero</h2>
    <div class="isiHero">
      <HeroShow v-for="(h, index) in hero" :key="h" :dataHero="h" :ind="index"></HeroShow>
    </div>
  </main>
  <Footer></Footer>
</template>

<script>
import Header from "./components/Header.vue";
import HeroShow from "./components/Hero.vue";
import Footer from "./components/Footer.vue";

const axios = require("axios").default;

export default {
  components: {
    Header,
    HeroShow,
    Footer,
  },
  name: "App",
  data() {
    return {
      hero: [
        {
          nama: "Aurora",
          type: "Mage",
          gambar: "aurora.jpg",
        },
        {
          nama: "Zilong",
          type: "Fighter",
          gambar: "zilong.jpg",
        },
        {
          nama: "Akai",
          type: "Tank",
          gambar: "akai.jpg",
        },
        {
          nama: "Bruno",
          type: "Marksman",
          gambar: "bruno.jpg",
        },
        {
          nama: "Gatot Kaca",
          type: "Tank",
          gambar: "gatotkaca.png",
        },
        {
          nama: "Layla",
          type: "Marksman",
          gambar: "layla.jpg",
        },
        {
          nama: "Nana",
          type: "Support",
          gambar: "nana.png",
        },
      ],
      current: 0,
    };
  },
  created() {
    axios({
      method: "get",
      url: "https://api.dazelpro.com/mobile-legends/hero",
      responseType: "stream",
    }).then(function(res) {
      console.log(res.data.hero);
    });
  },
  methods: {
    gantiHero: function() {
      let rand = Math.floor(Math.random() * this.hero.length);
      this.current = rand;
    },
  },
  computed: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* margin-top: 60px; */
}

* {
  margin: 10px;
}

ul li {
  list-style: none;
}

.isiHero {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  justify-content: start;
}
</style>
