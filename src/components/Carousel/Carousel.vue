<template>
  <div class="carousel">
    <slot></slot>
    <h1>{{ title }}</h1>
    <carousel-slide>
      <img src="http://lorempicsum.com/futurama/630/300/1" alt="" class="carousel_slide">
      <h2>Slide 1</h2>
    </carousel-slide>
    <carousel-slide>
      <img src="http://lorempicsum.com/futurama/630/300/1" alt="" class="carousel_slide">
      <h2>Slide 2</h2>
    </carousel-slide>
    <button class="carousel_nav carousel_next" @click.prevent="next"></button>
    <button class="carousel_nav carousel_prev" @click.prevent="prev"></button>
  </div>
</template>

<script>
  import CarouselSlide from '@/components/Carousel/Slides/CarouselSlides'

  export default {
    name: 'Carousel',
    data () {
      return {
        title: 'Carousel',
        index: 0,
        slides: []
      }
    },
    mounted () {
      this.slides = this.$children
      this.slides.forEach((slide, i) => {
        slide.index = i
      })
    },
    computed: {
      slidesCount () { return this.slides.length }
    },
    components: {
      CarouselSlide
    },
    methods: {
      next () {
        this.index++
        if (this.index >= this.slidesCount) {
          this.index = 0
        }
      },
      prev () {
        this.index--
        if (this.index < 0) {
          this.index = this.slidesCount - 1
        }
      }
    }
  }
</script>

<style>
  h1 {
    text-align: center;
    text-transform: uppercase;
  }
  .carousel {
    overflow: hidden;
    position: relative;
    width: 60%;
    display: block;
    margin: 0 auto;
  }
  .carousel_nav {
    position: absolute;
    top:50%;
    background: rgba(0,0,0,.5);
    width: 50px;
    height:50px;
    left:10px;
  }

  .carousel_next {
    right:10px;
    left:auto;
  }

  .carousel_slide {
    width: 100%;
    height: auto;
  }

   h2 {
     width: 100%;
     position: absolute;
     top:50%;
     font-size:20px;
     font-family:sans-serif;
     text-transform: uppercase;
     color:#fff;
     text-align: center;
   }
</style>
