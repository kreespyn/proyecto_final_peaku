<template>
  <div id="app">
    <MyHeader/>
    <MyComponent :locations="locations"/>
    <VacationComponent :locations="locations"/>
    <MyCarousel :locations="locations"/>
    <MyUpdate :locations="locations"/>
    <MyFooter :locations="locations"/>
  </div>
</template>

<script>
import axios from 'axios'
import MyComponent from './components/MyComponent.vue'
import MyHeader from './components/MyHeader.vue'
import VacationComponent from './components/VacationComponent.vue'
import MyCarousel from './components/MyCarousel.vue'
import MyUpdate from './components/MyUpdate.vue'
import MyFooter from './components/MyFooter.vue'



export default {
  name: 'App',
  components: {
    MyComponent,
    MyHeader,
    VacationComponent,
    MyCarousel,
    MyUpdate,
    MyFooter
},
  data() {
    return {
      locations: []
    }
  },
  created() {
    axios.get('http://localhost:8000/locations/')
      .then(response => {
        this.locations = response.data
      })
  }
}
</script>

<style scoped>
  #app {
    margin-right: 15rem;
    margin-left: 15rem;
  }
</style>