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
    };
  },

  methods: {
    getRandomNum() {
      return Math.floor(Math.random() * 500);
    },

    getRandomPics() {
      for (let i = 1; i <= 10; i++) {
        const picPlaceholder =
          "https://www.baywoodglass.ca/wp-content/uploads/2017/05/placeholder-300x200.png";

        let picUrl = `https://picsum.photos/id/${this.getRandomNum()}/300/200`;

        // CHECK URL
        const http = new XMLHttpRequest();
        http.open("GET", picUrl, false);
        http.send();
        // FILL ARRAY

        if (http.status != 404) this.pictures.push(picUrl);
        else this.pictures.push(picPlaceholder);
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
    &:hover {
      // box-shadow: 0 5px 8px darkslategrey;
      transform: translateY(10px);
      box-shadow: 0 -5px 8px $primary-color;
    }
  }
}
</style>