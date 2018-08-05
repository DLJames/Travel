<template>
    <div class="home-recommend">
        <div class="title">猜你喜欢</div>
        <ul>
            <li class="item border-bottom" v-for="item in recomendList" :key="item.id">
                <img class="item-img" :src="item.imgUrl" />
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-btn">查看详情</button>
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
                        imgUrl: 'http://img1.qunarzz.com/sight/p0/1602/39/39f6b1003abe1b2790.img.jpg_200x200_a7051b04.jpg',
                        title: '老虎滩海洋公园',
                        desc: '16485条评论'
                    },
                    {
                        id: '002',
                        imgUrl: 'http://img1.qunarzz.com/sight/p0/1703/94/944fc059260bd728a3.water.jpg_200x200_742cb84f.jpg',
                        title: '海昌发现王国',
                        desc: '17080条评论'
                    },
                    {
                        id: '003',
                        imgUrl: 'http://img1.qunarzz.com/sight/p0/1707/57/5729585581b6732fa3.water.jpg_200x200_85298361.jpg',
                        title: '大连森林动物园',
                        desc: '14210条评论'
                    }
                ]
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl';
    .home-recommend
        width 100%
        .title
            background-color #eee
            line-height .8rem
            text-indent .3rem
            margin-top .2rem
        .item
            overflow hidden
            height 1.9rem
            display flex
            .item-img
                height 1.7rem
                width 1.7rem
                padding .1rem
            .item-info
                flex 1
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
                .item-btn
                    background-color #ff9300
                    padding 0 .2rem
                    border-right .06rem
                    margin-top .16rem
                    line-height .44rem
                    border-radius .06rem
                    color #fff
                    ellipsis()
</style>

