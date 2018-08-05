<template>
    <div class="header-swiper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <swiper-slide v-for="(item) in swiperList" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl" />
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
         </swiper>
    </div>
</template>

<script>
export default {
  name: "HomeSwiper",
  data() {
    return {
        swiperOption: {
            pagination: '.swiper-pagination',
            loop: true
        }
    }
  },

  props: {
      swiperList: Array
  },

  computed: {
      showSwiper () {
          return this.swiperList.length;
      }
  }
};
</script>

<style lang="stylus" scoped>
.header-swiper >>> .swiper-pagination-bullet-active
    background #fff
.header-swiper
    width 100%
    height 0
    overflow hidden
    background-color #ccc
    padding-bottom 26.66%
    .swiper-img
        width 100%
</style>
