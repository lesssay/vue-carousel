<template>
  <footer>
    <nav>
      <div class="contacts">
        <h3>CONTACTS</h3>
        <ul>
          <li>
            <a href="tel:3896947979"
              ><i class="fa-solid fa-phone"></i> 3896947979</a
            >
          </li>
          <li>
            <a href="mailto:giorgia9288@gmail.com"
              ><i class="fa-solid fa-envelope"></i> giorgia9288@gmail.com</a
            >
          </li>
        </ul>
      </div>

      <div class="social">
        <h3>SOCIAL</h3>
        <ul>
          <li>
            <a href="www.facebook.com/giorgia.mendico"
              ><i class="fa-brands fa-facebook"></i
            ></a>
          </li>
          <li>
            <a href="www.instagram.com/giorgiamendico"
              ><i class="fa-brands fa-instagram"></i
            ></a>
          </li>
          <li>
            <a href="www.linkedin.com/in/lesssay"
              ><i class="fa-brands fa-linkedin"></i
            ></a>
          </li>
        </ul>
      </div>
    </nav>
  </footer>
</template>
  
<script>
export default {
  name: "AppFooter",
  components: {},
};
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  justify-content: space-between;

  h3 {
    margin-bottom: 10px;
  }

  .contacts li {
    font-size: 0.8rem;
  }

  .social {
    h3 {
      text-align: end;
    }
    ul {
      display: flex;
      li {
        font-size: 1.8rem;
        margin-left: 20px;
      }
    }
  }
}
</style>
  