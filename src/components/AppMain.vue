<template>
  <main>
    <h1>FIRST CAROUSEL</h1>
    <AppCarouselFirst class="first-carousel" />
    <h1>SECOND CAROUSEL</h1>
    <AppCarouselSecond />
  </main>
</template>

<script>
import AppCarouselFirst from "./AppCarouselFirst.vue";
import AppCarouselSecond from "./AppCarouselSecond.vue";

export default {
  name: "AppMain",
  components: {
    AppCarouselFirst,
    AppCarouselSecond,
  },
};
</script>

<style>
h1 {
  text-align: center;
  margin-bottom: 20px;
  color: rgb(26, 26, 26);
  text-shadow: 0 5px 5px darkslategrey;
}
main {
  padding: 100px 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.first-carousel {
  margin-bottom: 100px;
}
</style>