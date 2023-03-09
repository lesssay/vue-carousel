<template>
  <main>
    <section class="first-carousel">
      <h1>First Carousel</h1>
      <AppCarouselFirst />
    </section>

    <section>
      <h1>Second Carousel</h1>
      <AppCarouselSecond />
    </section>
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

<style lang="scss" scoped>
@import "../assets/sass/variables";

main {
  padding: 100px 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .first-carousel {
    margin-bottom: 100px;
  }

  h1 {
    text-align: center;
    margin-bottom: 20px;
    color: $secondary-color;
    text-shadow: 0 3px 7px $primary-color;
    font-size: 1.8rem;
  }
}
</style>