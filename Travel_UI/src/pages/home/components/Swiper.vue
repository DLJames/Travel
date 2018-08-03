<template>
    <div class="header-swiper">
        <swiper :options="swiperOption">
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
        },
        swiperList: [
            {
                id: '0001',
                imgUrl: 'http://img1.qunarzz.com/piao/fusion/1806/de/df09fa61aed2d502.jpg_750x200_67472739.jpg'
            },
            {
                id: '0002',
                imgUrl: 'http://img1.qunarzz.com/piao/fusion/1808/3a/994bd8bedc881e02.jpg_750x200_2f656a21.jpg'
            },
            {
                id: '0003',
                imgUrl: 'http://img1.qunarzz.com/piao/fusion/1806/3c/c72a1ccd4d7b2202.jpg_750x200_b88bbab4.jpg'
            }
        ]
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
