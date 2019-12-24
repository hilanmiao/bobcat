<template>
  <section class="hero is-fullheight">
    <!-- Hero head: will stick at the top -->
    <div class="hero-head">
      <nav class="navbar">
        <div class="container">
          <div class="navbar-brand">
            <a class="navbar-item has-text-white" href="/">
              <img src="~assets/logo.png" alt="" width="150" style="max-height: fit-content;">
            </a>
          </div>
        </div>
      </nav>
    </div>

    <!-- Hero content: will be in the middle -->
    <div class="hero-body">
      <div class="container has-text-centered">
        <h1 class="title has-text-white is-size-1">
          游戏展示
        </h1>
        <h2 class="subtitle has-text-white is-uppercase">
          introduction to the game
        </h2>
        <div v-swiper:mySwiper="swiperOption" v-if="banners.length > 0">
          <div class="swiper-wrapper">
            <div v-for="banner in banners" class="swiper-slide">
              <img :src="banner">
            </div>
          </div>
<!--          <div class="swiper-pagination swiper-pagination-bullets" />-->
        </div>
      </div>
    </div>

    <!-- Hero footer: will stick at the bottom -->
    <div class="hero-foot" style="padding: 2rem;">
      <div class="content has-text-centered has-text-white">
        <p>
          <strong class="has-text-white">Game</strong> platform maked by <a class="has-text-white" href="https://github.com/hilanmiao">https://github.com/hilanmiao</a>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
// import Logo from '~/components/Logo.vue'

export default {
  data () {
    return {
      banners: [],
      swiperOption: {
        effect: 'coverflow',
        autoplay: {
          disableOnInteraction: false,
          delay: 3000
        },
        grabCursor: true,
        // loop: true,
        // loopAdditionalSlides: 2,
        // loopedSlides: 5,
        initialSlide: 3,
        slidesPerView: 'auto',
        centeredSlides: true,
        // pagination: {
        //   el: '.swiper-pagination',
        //   dynamicBullets: true
        // },
        coverflowEffect: {
          rotate: 0,
          stretch: 30,
          depth: 100,
          modifier: 3,
          slideShadows: false
        },
        on: {
          slideChange () {
            // console.log('onSlideChangeEnd', this)
          },
          tap: () => {
            // console.log('onTap', this)
            this.handleTap()
          }
        }
      }
    }
  },
  mounted () {
    console.log('app init', this)
    this.init()
    console.log(
      'This is current swiper instance object', this.mySwiper,
      'I will slideTo banners 3')
    // this.mySwiper.slideTo(3)
  },
  methods: {
    init () {
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
      this.banners.push('/screenshot1.png')
    },
    handleTap () {
      // const activeIndex = this.mySwiper.activeIndex
      const clickedIndex = this.mySwiper.clickedIndex
      if (clickedIndex !== undefined) {
        this.mySwiper.slideTo(clickedIndex)
        setTimeout(() => {
          this.$router.push('game')
        }, 1000)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  h2 {
    padding-bottom: 2rem;
  }

  .swiper-container {
    height: 450px;
    width: 100%;

    .swiper-slide {
      /*position: relative;*/
      width: 325px;
      text-align: center;
      font-size: 38px;
      font-weight: 700;
      /*background-color: #eee;*/
      display: flex;
      justify-content: center;
      align-items: center;
      background-image: url(~assets/image/border3.png);
      background-repeat: no-repeat;
      background-size: 100% 100%;

      img {
        width: 90%;
        height: 90%;
        padding: 2%;
      }
    }

    .swiper-pagination {
      > .swiper-pagination-bullet {
        background-color: red;
      }
    }
  }
</style>
