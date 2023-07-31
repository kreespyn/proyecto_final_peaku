<template>
    <b-footer class="mx-0 pt-0 px-0">
      <b-row class="mt-5">
        <b-col cols="6">
          <b-nav>
            <b-nav-item class="my-nav-item">
              <b-row>
                <b-img :src="require('@/assets/Logo.png')" alt="Logo Pagina" title="Logo" class="mb-3 p-0 logo-img" thumbnail rounded="false" width="20" height="4" />
                <p class="px-0">Book your trip in minute, get full <br/> Control for much longer.</p>
              </b-row>
            </b-nav-item>
          </b-nav>
        </b-col>
        <b-col cols="2">
          <b-nav>
            <b-nav-item class="my-nav-item">
              <b-row>
                <h5>Company</h5>
                <p>About</p>
                <p>Careers</p>
                <p>Logistic</p>
                <p>Privacy & Policy</p>
              </b-row>
            </b-nav-item>
          </b-nav>
        </b-col>
        <b-col cols="2">
          <b-nav>
            <b-nav-item class="my-nav-item">
              <b-row>
                <h5>Contact</h5>
                <p>Help/FAQ</p>
                <p>Press</p>
                <p>Affilates</p>
              </b-row>
            </b-nav-item>
          </b-nav>
        </b-col>
        <b-col cols="2">
          <b-nav>
            <b-nav-item class="my-nav-item">
              <b-row>
                <h5>More</h5>
                <p>Press Centre</p>
                <p>Our Blog</p>
                <p>Low fare tips</p>
              </b-row>
            </b-nav-item>
          </b-nav>
        </b-col>
      </b-row>
      <b-row>
        <b-img :src="require('@/assets/Border.png')" alt="Border image" />
      </b-row>
      <b-container >
        <b-row class="d-flex justify-content-between mt-5">
          <b-col cols="9"><p>Copyright, Trabook 2022. All rights reserved.</p></b-col>
          <b-col cols="3"><p>Terms & Conditions</p></b-col>
        </b-row>
      </b-container>
    </b-footer>
  </template>
  
  <script>
  export default {
   
  }
  </script>
  
  <style scoped>
.logo-img {
  width: 130px;
  height: 24px;
}

.my-nav-item a {
    color: lightslategray !important;
  }
</style>