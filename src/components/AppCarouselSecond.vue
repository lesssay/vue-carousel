<template>
  <div
    class="carousel"
    @mousedown="handleMouseDown"
    @mouseup="handleMouseUp"
    @mousemove="handleMouseMove"
  >
    <div class="slides" :style="{ transform: transformValue }">
      <div class="slide" v-for="(slide, index) in slides" :key="index">
        <img :src="slide" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slides: [],
      currentIndex: 0,
      startX: 0,
      isDragging: false,
    };
  },
  computed: {
    transformValue() {
      return `translateX(-${this.currentIndex * 25}%)`;
    },
  },
  methods: {
    handleMouseDown(event) {
      this.startX = event.clientX;
      console.log(event.clientX);
      this.isDragging = true;
    },
    handleMouseUp(event) {
      const endX = event.clientX;
      console.log(event.clientX);
      const diff = endX - this.startX;
      if (diff > 0 && this.currentIndex > 0) {
        this.currentIndex--;
      } else if (diff < 0 && this.currentIndex < this.slides.length - 1) {
        this.currentIndex++;
      }
      this.isDragging = false;
    },
    handleMouseMove(event) {
      if (this.isDragging) {
        event.preventDefault();
      }
    },
    getRandomNum() {
      return Math.floor(Math.random() * 500);
    },

    getRandomSlides() {
      for (let i = 1; i <= 10; i++) {
        const slidePlaceholder =
          "https://www.baywoodglass.ca/wp-content/uploads/2017/05/placeholder-300x200.png";

        let slideUrl = `https://picsum.photos/id/${this.getRandomNum()}/300/200`;

        // CHECK URL
        const http = new XMLHttpRequest();
        http.open("GET", slideUrl, false);
        http.send();
        // FILL ARRAY

        if (http.status != 404) this.slides.push(slideUrl);
        else this.slides.push(slidePlaceholder);
      }
    },
  },

  mounted() {
    this.getRandomSlides();
  },
};
</script>

<style>
.carousel {
  width: 100%;
  overflow: hidden;
  position: relative;
}

.carousel__viewport {
  padding: 10px 0;
}

.slides {
  display: flex;
  width: 100%;
  padding: 20px 0;
  transition: transform 0.5s ease-out;
}
.slide {
  flex: 0 0 100%;
  flex-basis: calc(100% / 4 - 20px);
  margin: 0 10px;
  border: solid 10px white;
  box-shadow: 0 5px 8px darkslategrey;
  text-align: center;
}

.slide:hover {
  transform: scale(1.1);
}

img {
  max-width: 100%;
}
</style>
