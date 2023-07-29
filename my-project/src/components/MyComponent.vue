<template>
  <b-container fluid class="p-0">
    <b-row class="mx-0">
      <b-col cols="6" class="d-flex flex-column justify-content-center align-items-start px-5">
        <h1 class="text-center" style="width:30rem; font-size: 3.8rem;">
          Get started your exciting
          <span style="color:#fa7436">journey</span> with us.
        </h1>
        <p class="mb-5"  style="width: 68%; font-size: 1.2rem;">
          A team of experienced tourism professionals will provide you with the best advice and tips for your desired place.
        </p>
        <b-button variant="outline-primary" class="mt-3 px-4 py-2 bg-white" style="color: #fa7436;border: 1px solid;">Discover Now</b-button>
      </b-col>
      <b-col cols="6" class="d-flex justify-content-center align-items-center">
        <b-img  :src="require('@/assets/tourist-with-thumb-up__1_-removebg 1.png')" alt="Imagen Viajero" />
      </b-col>
    </b-row>
    <b-row>
      <b-row class="mx-0">
        <b-col class="text-center">
          <h2 class="mt-5">Things you need<span style="color: #fa7436;">&nbsp;to do</span></h2>
          <p class="font-weight-light">We ensure that you’ll embark on a perfectly planned,<br> safe vacation at a price you can afford.</p>
        </b-col>
      </b-row>
      <b-row class="mx-0 justify-content-center" style="margin-bottom: 5.5rem;">
        <b-col lg="3" class="bg-white rounded-2 m-3 p-2 text-center shadow">
          <b-img :src="require('@/assets/Group (1).png')" alt="Logo Pagina" title="Logo" class="m-3 justify-content-end"></b-img>
          <h4 class="m-3 mt-5">Sign Up</h4>
          <p class="m-3 font-weight-light">Completes all the work associated with planning and processing</p>
        </b-col>
        <b-col lg="3" class="bg-white rounded-2 m-3 p-2 text-center shadow">
          <b-img :src="require('@/assets/Group.png')" alt="Logo Pagina" title="Logo" class="m-3 justify-content-end"></b-img>
          <h4 class="m-3 mt-5">Worth of Money</h4>
          <p class="m-3 font-weight-light">After successful access then book from exclusive deals & pricing</p>
        </b-col>
        <b-col lg="3" class="bg-white rounded-2 m-3 p-2 text-center shadow">
          <b-img :src="require('@/assets/Group (2).png')" alt="Logo Pagina" title="Logo" class="m-3 justify-content-end"></b-img>
          <h4 class="m-3 mt-5">Exciting Travel</h4>
          <p class="m-3 font-weight-light">Start and explore a wide range of exciting travel experience.</p>
        </b-col>
      </b-row>
    </b-row>

    <b-row class="mx-2">
        <div class="col-md-12 col-lg-12 d-flex justify-content-center align-items-center mb-5">
    <b-nav class="bg-white rounded-2 shadow-lg">
      <ul class="d-flex justify-content-between mb-0 p-3 list-unstyled" style="width: 52.563rem">
        <li class="m-3 pr-5">
          <span>Location&nbsp;<b-img :src="require('@/assets/Vector 4855.png')" title="Logo" alt="Logo Pagina" width="13" height="8"></b-img><br>
            <span style="font-weight: lighter; font-size: 75%;">Where are you going</span>
          </span>
        </li>
        <li class="m-3 pr-5">
          <span>Date&nbsp;<b-img :src="require('@/assets/Vector 4855.png')" title="Logo" alt="Logo Pagina" width="13" height="8"></b-img><br>
            <span style="font-weight: lighter; font-size: 75%;">When you will go</span>
          </span>
        </li>
        <li class="m-3 pr-5">
          <span>Guest&nbsp;<b-img :src="require('@/assets/Vector 4855.png')" title="Logo" alt="Logo Pagina" width="13" height="8"></b-img><br>
            <span style="font-weight: lighter; font-size: 75%;">Number of guest</span>
          </span>
        </li>
        <li class="d-flex flex-column justify-content-center pr-5 m-3">
          <b-button variant="primary" class="shadow-lg" style="background-color: #fa7436; border:none;">Explore Now</b-button>
        </li>
      </ul>
    </b-nav>
  </div>
    </b-row>

    <b-container fluid class="d-flex flex-column align-items-center justify-content-center" style="background: #FEFCFB; margin-top: 4.5rem;">
      <b-row>
        <b-col class="text-center">
          <h2 class="mt-3">Exclusive<span  style="color: #FA7436;">&nbsp;deals & discounts</span></h2>
          <p class="font-weight-light">Discover our fantastic early booking discounts <br> & start planning your journey.</p>
        </b-col>
      </b-row>
    </b-container>

    <b-row class="d-flex justify-content-center align-items-center" style="background: #FEFCFB;">
      <b-col cols="12" md="6" lg="2" xl="2" class="m-3 p-0" v-for="location in locations" :key="location.id">
        <b-card :img-src="getImage(location.image)" img-alt="Image" class="mb-3 hoverable-card" img-top
        @mouseover="hovered = location.id" 
        @mouseleave="hovered = null">
  <div class="hover-overlay" v-if="hovered === location.id">
    <b-img :src="require('@/assets/Hover effect.png')" class="hover-image"  />
  </div>
  <b-card-title>{{ location.name }}</b-card-title>
  <b-card-text class="text-muted">{{ location.country }}</b-card-text>
</b-card>
      </b-col>
    </b-row>

    <b-row class="mb-5">
      <b-col class="text-center">
        <b-button class="d-inline-block" variant="link" @click="previousPage" :disabled="pageIndex === 0">
          <b-img class="m-2 rounded-circle" style="border-style: solid; border-color: silver; width: 2rem; padding: 5px 5px;" :src="require('@/assets/Arrow 3 (1).png')" title="Logo" alt="Logo Pagina"/>
        </b-button>
        <b-button class="d-inline-block" variant="link" @click="nextPage" :disabled="pageIndex === 3">
          <b-img class="m-2 p-2 rounded-circle" style="background-color: #FA7436; width: 2rem;" :src="require('@/assets/Arrow 3 (2).png')" title="Logo" alt="Logo Pagina"/>
        </b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  props: {
    initialLocations: Array
  },
  data() {
    return {
      images: require.context('@/assets/', false, /\.png$/),
      locations: this.initialLocations,
      pageIndex: 0,
      itemsPerPage:3,
      hovered: null
    };
  },
  created() {
    this.fetchLocations(); // Call the method to fetch data when the component is created.
  },
  methods: {
    getImage(imageName) {
      return this.images(`./${imageName}`);
    },
    async fetchLocations() {
      const response = await fetch('http://localhost:8000/locations/?skip=' + (this.pageIndex * this.itemsPerPage) + '&limit=' + this.itemsPerPage);
      this.locations = await response.json();
    },
    nextPage() {
      this.pageIndex++;
      this.fetchLocations();
    },
    previousPage() {
      if (this.pageIndex > 0) {
        this.pageIndex--;
        this.fetchLocations();
      }
    }
  }
}
</script>

<style scoped>
.hoverable-card {
  position: relative;
}

.hover-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: opacity 0.3s;
}

.hover-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

</style>