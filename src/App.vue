<template>
  <div class="app">
    <carousel 
      @next="next"
      @prev="prev">
      
      <carousel-slide v-for="(slide, index) in slides" 
        :key="slide" 
        :index="index"
        :visibleSlide = "visibleSlide"
        :direction="direction">
        <img :src="slide" />
      </carousel-slide>
    </carousel>
  </div>
</template>

<script>
import Carousel from './components/Carousel';
import CarouselSlide from './components/CarouselSlide';
export default {
  data() {
    return{
      slides: [
        'https://picsum.photos/id/237/600/350',
        'https://picsum.photos/id/236/600/350',
        'https://picsum.photos/id/235/600/350',
        'https://picsum.photos/id/234/600/350',
        'https://picsum.photos/id/233/600/350',
        'https://picsum.photos/id/232/600/350',
      ],
      visibleSlide: 0,
      direction: 'left',
    }
  },
  computed: {
    slidesLen(){
      return this.slides.length;
    }
  },
  methods :{
    next(){
      if(this.visibleSlide >= this.slidesLen - 1){
        this.visibleSlide = 0;
      } else{ 
        this.visibleSlide++;
      }
      this.direction = "left"
    },
    prev(){
      if(this.visibleSlide <= 0){
        this.visibleSlide = this.slidesLen - 1
      } else{ 
        this.visibleSlide--;
      }
      this.direction = "right"

    }
  },
  components: { 
    Carousel, 
    CarouselSlide,
  }
}
</script>

<style>
  .app{
    display: flex;
    justify-content: center;
  }
</style>