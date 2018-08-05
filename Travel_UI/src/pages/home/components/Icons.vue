<template>
    <div class="home-icons">
        <swiper :options="swiperOption">
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
          loop: true
      },
      iconList: [
        {
          id: "0001",
          name: "景点门票",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png"
        },
        {
          id: "0002",
          name: "一日游",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png"
        },
        {
          id: "0003",
          name: "游乐场",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png"
        },
        {
          id: "0004",
          name: "动植物园",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png"
        },
        {
          id: "0005",
          name: "大连必游",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png"
        },
        {
          id: "0006",
          name: "海洋馆",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png"
        },
        {
          id: "0007",
          name: "汽车票",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png"
        },
        {
          id: "0008",
          name: "夏日玩水",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png"
        },
        {
          id: "0009",
          name: "演出",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png"
        },
        {
          id: "0010",
          name: "全部玩乐",
          imgUrl:
            "http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png"
        }
      ]
    };
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
      }
  },

  mounted () {
      console.log('===',this.pages)
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
