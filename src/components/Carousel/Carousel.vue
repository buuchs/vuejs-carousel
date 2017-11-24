<template>
  <div class="Carousel">
    <slot></slot>
    <h1>{{ title }}</h1>
    <carousel-slide>
      <img src="http://lorempicsum.com/futurama/630/300/1" alt="">
      salut les gens
    </carousel-slide>
    <carousel-slide>
      Au revoir les gens
      <img src="http://lorempicsum.com/futurama/630/300/1" alt="">
    </carousel-slide>
    <button class="carousel_nav carousel_next" @click.prevent="next">Suivant</button>
    <button class="carousel_nav carousel_prev" @click.prevent="prev">Précédent</button>
  </div>
</template>

<script>
  import CarouselSlide from '@/components/Carousel/Slides/CarouselSlides'

  export default {
    name: 'Carousel',
    data () {
      return {
        title: 'Crarousel',
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
