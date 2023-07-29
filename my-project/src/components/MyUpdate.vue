<template>
        <b-container fluid class="p-0">
          <b-row class="mx-5">
            <b-col cols="6" class="d-flex flex-column justify-content-center align-items-start px-5">
            </b-col>
          </b-row>
          <b-row>
            <b-row class="mx-0">
              <b-col class="text-center">
                <h2 class="mt-5">Get update with<span style="color: #fa7436;">&nbsp;latest blog</span></h2>
              </b-col>
            </b-row>
          </b-row>
          <b-row class="mb-5">
          </b-row>
          <b-row class="d-flex justify-content-center align-items-center" style="background: #FEFCFB;">
            <b-col cols="12" md="6" lg="2" xl="2" class="m-3 p-0" v-for="location in locations" :key="location.id">
              <b-card :img-src="getImage(location.image)" img-alt="Image" class="mb-3" img-top>
                <b-card-title>{{ location.name }}</b-card-title>
                <b-card-text class="text-muted">{{ location.country }}</b-card-text>
              </b-card>
            </b-col>
          </b-row>
          <b-col class="text-center">
            <b-button class="d-inline-block m-2" variant="link" style="width: 1.5rem; height: 1.5rem; border-radius: 50%; border: solid 1px silver;background-color: silver" @click="previousPage" :disabled="pageIndex === 0"></b-button>
            <b-button class="d-inline-block m-2" variant="link" style="width: 1.5rem; height: 1.5rem; border-radius: 50%; background-color: #FA7436;"></b-button>
            <b-button class="d-inline-block m-2" variant="link" style="width: 1.5rem; height: 1.5rem; border-radius: 50%; border: solid 1px silver;background-color: silver" @click="nextPage" :disabled="pageIndex === 2"></b-button>
          </b-col>
          
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
          this.fetchLocations();
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
