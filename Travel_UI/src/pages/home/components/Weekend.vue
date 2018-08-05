<template>
    <div class="home-weekend">
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item border-bottom" v-for="item in recomendList" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl" />
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'HomeRecommend',
        data () {
            return {
                recomendList: [
                    {
                        id: '001',
                        imgUrl: 'http://img1.qunarzz.com/sight/source/1505/b7/8a08a1023062b3.jpg_r_640x214_d7cb475c.jpg',
                        title: '最赞的海滨浴场',
                        desc: '跳进海里，享受铺天盖地的清凉吧'
                    },
                    {
                        id: '002',
                        imgUrl: 'http://img1.qunarzz.com/sight/source/1505/7f/fa4eb0ca72409d.jpg_r_640x214_2f2a860e.jpg',
                        title: '大连必游TOP10',
                        desc: '爱上北方的碧海蓝天'
                    },
                    {
                        id: '003',
                        imgUrl: 'http://img1.qunarzz.com/sight/source/1507/6b/70d17d828d87e1.jpg_r_640x214_6a995270.jpg',
                        title: '周末游首选',
                        desc: '当地人经常出没的地方'
                    }
                ]
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl';
   .home-weekend
        width 100%
        .title
            background-color #eee
            line-height .8rem
            text-indent .3rem
            margin-top .2rem
        .item-img-wrapper
            overflow hidden
            height 0
            padding-bottom 33.9%
            .item-img
                width 100%
        .item-info
            padding .1rem
            min-width 0
            .item-title
                line-height .54rem
                font-size .32rem
                ellipsis()
            .item-desc
                line-height .4rem
                color #ccc
                ellipsis()
</style>

