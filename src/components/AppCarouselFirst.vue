<template>
  <carousel :items-to-show="4" :items-to-scroll="4" :wrap-around="false">
    <slide v-for="(slide, i) in pictures" :key="slide">
      <img :src="slide" :alt="i" />
    </slide>

    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
</template>

<script>
// If you are using PurgeCSS, make sure to whitelist the carousel CSS classes

import "../../node_modules/vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

export default {
  name: "AppCarouselFirst",
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },

  data() {
    return {
      pictures: [],
      picsCount: 10,
      // picPlaceholder:
      //   "https://www.baywoodglass.ca/wp-content/uploads/2017/05/placeholder-300x200.png",
    };
  },

  methods: {
    getRandomPics() {
      function getRandomNum() {
        return Math.floor(Math.random() * 1000) + 1;
      }
      const usedNums = []; // array vuoto per memorizzare i numeri già generati

      // for (let i = 0; i < this.picsCount; i++) {
      while (this.pictures.length < this.picsCount) {
        let picNum;
        do {
          picNum = getRandomNum();
        } while (usedNums.includes(picNum)); // genera un nuovo numero finché non viene generato un numero che non è già stato usato

        usedNums.push(picNum); // aggiungi il numero casuale all'array dei numeri già generati

        const picUrl = `https://picsum.photos/id/${picNum}/300/200`;

        // controllo l'url
        const http = new XMLHttpRequest();
        http.open("GET", picUrl, false);
        http.send();

        // riempio l'array
        if (http.status == 200) this.pictures.push(picUrl);
        // else this.pictures.push(this.picPlaceholder);
      }
    },
  },

  mounted() {
    this.getRandomPics();
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/sass/variables";
.carousel__viewport {
  padding: 20px;
  // .carousel__slide {
  //    margin: 10px;
  //    border: solid 10px white;
  // }

  img {
    width: 90%;
    height: 90%;
    margin: 0 10px;
    border: 1px solid $bg-color;
    &:hover {
      // box-shadow: 0 5px 8px darkslategrey;
      transform: translateY(10px);
      box-shadow: 0 -5px 8px $primary-color;
    }
  }
}
</style>