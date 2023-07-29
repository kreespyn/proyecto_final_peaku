<template>
    <b-container fluid class="p-0">
      <b-row class="mx-0">
        <b-col cols="6" class="d-flex flex-column justify-content-center align-items-start px-5">
        </b-col>
       
      </b-row>
      <b-row>
        <b-row class="mx-0">
          <b-col class="text-center">
            <h2 class="mt-5">Best<span style="color: #fa7436;">&nbsp;vacation plan</span></h2>
            <p class="font-weight-light">Plan your perfect vacation with our travel agency. Choose<br> among hundreds of all-inclusive offers!</p>
          </b-col>
          
        </b-row>
        
        
      </b-row>
      <b-row class="mb-5">
        <b-col class="text-center">
          <b-button class="d-inline-block" variant="link" @click="previousPage" :disabled="pageIndex === 0">
            <b-img class="m-2 rounded-circle" style="border-style: solid; border-color: silver; width: 2rem; padding: 5px 5px;" :src="require('@/assets/Arrow 3 (1).png')" title="Logo" alt="Logo Pagina"/>
          </b-button>
          <b-button class="d-inline-block" variant="link" @click="nextPage" :disabled="pageIndex === 2">
            <b-img class="m-2 p-2 rounded-circle" style="background-color: #FA7436; width: 2rem;" :src="require('@/assets/Arrow 3 (2).png')" title="Logo" alt="Logo Pagina"/>
          </b-button>
        </b-col>
      </b-row>

      <b-row class="d-flex justify-content-center align-items-center" style="background: #FEFCFB;">
        <b-col cols="12" md="6" lg="2" xl="2" class="m-3 p-0" v-for="location in locations" :key="location.id">
          <b-card :img-src="getImage(location.image)" img-alt="Image" class="mb-3" img-top>
            <b-card-title>{{ location.name }}</b-card-title>
            <b-card-text class="text-muted">{{ location.country }}</b-card-text>
          </b-card>
        </b-col>
      </b-row>
      <b-row class="mx-5">
        <b-col sm="12" md="6" class="d-flex flex-column justify-content-center align-items-start px-0">
          <h2 style="margin-top: 2.5rem;">What people say
              <span  style="color: #FA7436;">about Us.</span></h2>
          <p class="mb-5"  style="width: 68%; font-size: 1.2rem; font-weight:lighter;">Our Clients send us bunch of smilies with our services and we love them.</p>
          <b-row class="justify-content-center mb-5">
            <b-img class="m-2 rounded-circle" style="border-style: solid; border-color: silver; width: 2rem; padding: 5px 5px;" :src="require('@/assets/Arrow 3 (1).png')" title="Logo" alt="Logo Pagina"/>
            <b-img class="m-2 p-2 rounded-circle" style="background-color: #FA7436; width: 2rem;" :src="require('@/assets/Arrow 3 (2).png')" title="Logo" alt="Logo Pagina"/>
          </b-row>
        </b-col>
        <b-col sm="12" md="6" class="d-flex justify-content-center align-items-center">
          <b-img :src="require('@/assets/cara.png')" title="Viajero" alt="Imagen Viajero"/>
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
        itemsPerPage: 3
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
  .btn-primary, .btn-primary:hover, .btn-primary:active, .btn-primary:visited {
    background-color: #fa7436 !important;
  }
  
  
  </style>