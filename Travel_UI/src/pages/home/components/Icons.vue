<template>
    <div class="home-icons">
        <swiper :options="swiperOption" v-if="showSwiper">
            <swiper-slide v-for="(page, index) in pages" :key="index">
            <!-- <swiper-slide> -->
                <div class="icon" v-for="item in page" :key="item.id">
                    <div class="icon-img-con">
                        <img class="icon-image" :src="item.imgUrl" />
                    </div>
                    <p class="icon-desc">{{item.name}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
  name: "HomeIcons",
  data() {
    return {
      swiperOption: {
          loop: true,
          autoplay: false
      }
    };
  },

  props: {
      iconList: Array
  },

  computed: {
      pages () {
          const pages = []
          this.iconList.forEach((item, index) => {
              let page = Math.floor(index / 8);
              if(!pages[page]) {
                  pages[page] = []
              }
              pages[page].push(item);
          });
          return pages;
      },

      showSwiper () {
          return this.iconList.length;
      }
  },

  mounted () {
  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
@import '~styles/mixins.styl';

    .home-icons >>> .swiper-container
        width: 100%;
        height: 0;
        padding-bottom: 50%;
    .home-icons 
        margin-top .2rem
        .icon 
            position: relative;
            width: 25%;
            height: 0;
            padding-bottom: 25%;
            float: left;
            overflow: hidden;
            .icon-img-con 
                position: absolute;
                left: 0;
                top: 0;
                right: 0;
                padding: 0.1rem;
                box-sizing: border-box;
                bottom: 0.44rem;
                .icon-image 
                    height: 100%;
                    display: block;
                    margin: 0 auto;
            .icon-desc 
                color: $darkTextColor;
                position: absolute;
                left: 0;
                right: 0;
                bottom: 0;
                line-height: 0.44rem;
                text-align: center;
                ellipsis()
</style>
