<template>
    <div class="city-list" ref="wraper">
        <div>
            <div class="area">
                <div class="title border-topbottom">您的位置</div>
                <div class="button-list">
                    <div class="button-wraper">
                        <div class="button">北京</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wraper" v-for="item in hot" :key="item.id">
                        <div class="button">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div class="item border-bottom" v-for="city in item" :key="city.id">{{city.name}}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import BScroll from 'better-scroll'

    export default {
        name: 'City',

        props: {
            cities: Object,
            hot: Array,
            letter: String
        },

        mounted () {
            this.scroll = new BScroll(this.$refs.wraper)
        },

        watch: {
            letter () {
                if(this.letter) {
                    const element = this.$refs[this.letter][0]

                    this.scroll.scrollToElement(element)
                }
            }
        },

        updated() {
            // this.scroll.resize()
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl';
    .border-topbottom
        &:before
            border-color #ccc
        &:after
            border-color #ccc
    .border-bottom
        &:before
            border-color #ccc
    .city-list
        position absolute
        top 1.58rem
        right 0
        left 0
        bottom 0
        overflow hidden
        .title
            line-height .54rem
            background-color #eee
            padding-left .2rem
            color #666
            font-size .26rem
        .button-list
            overflow hidden
            padding .1rem .6rem .1rem .1rem
            .button-wraper
                width 33.33%
                float left
                .button
                    border .02rem solid #ccc
                    border-radius .06rem
                    padding .1rem 0
                    text-align center
                    margin .1rem
        .item-list
            .item
                line-height .76rem
                padding-left .2rem
</style>
