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
            return {}
        },

        props: {
            recomendList: Array
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

