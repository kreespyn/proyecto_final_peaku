<template>
    <b-container fluid>
      <b-row align-h="center">
        <b-col cols="12" md="8" lg="6">
          <b-carousel
            ref="myCarousel"
            id="carousel-fade"
            style="text-shadow: 0px 0px 2px #000"
            fade
            img-width="100%"
            img-height="100%"
            controls
            class="custom-carousel"
          >
            <b-carousel-slide
              v-for="location in locations"
              :key="location.id"
              :caption="location.name"
              :img-src="getImage(location.image)"
            ></b-carousel-slide>
          </b-carousel>
        
        </b-col>
      </b-row>
    </b-container>
  </template>
  
  <style scoped>
  .carousel-indicators li {
    width: 20px;
    height: 20px;
    background-color: #ffa500; /* Change to any color you want */
  }

  .carousel-indicators .active {
    background-color: #ff0000; /* Change to any color you want */
  }
</style>

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
      itemsPerPage: 4
    };
  },
  created() {
    this.fetchLocations(); // Call the method to fetch data when the component is created.
  },
  methods: {
    nextSlide() {
      this.$refs.myCarousel.next()
    },
    prevSlide() {
      this.$refs.myCarousel.prev()},
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