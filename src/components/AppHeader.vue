<template>
  <header>
    <nav>
      <a class="logo" href=""><img src="../assets/img/logo.png" alt="" /></a>
      <a href="./AppMain.vue">CAROUSEL</a>
    </nav>
  </header>
</template>
  
<script>
export default {
  name: "AppHeader",
  components: {},
};
</script>

<style lang="scss">
nav {
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .logo {
    height: 100%;
    img {
      height: 100%;
    }
  }
}
</style>
  