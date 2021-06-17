<template>
  <div class="home">
    <Carousel msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Carousel from '@/components/Carousel.vue'

export default {
  name: 'Home',
  components: {
    Carousel
  }
}
</script>
