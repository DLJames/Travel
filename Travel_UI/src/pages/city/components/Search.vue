<template>
    <div>
        <div class="search">
            <input class="search-input" type="text" placeholder="请输入城市名或拼音" v-model="keyWord"/>
        </div>
        <div class="search-content" ref="scrollView" v-show="keyWord">
            <ul>
                <li class="search-item border-bottom" v-for="item in list" :key="item.id" @click="changeCity(item.name)">{{item.name}}</li>
                <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
            </ul>
        </div>
    </div>
</template>

<script>
    import BScroll from 'better-scroll'

    export default {
        name: 'City',
        data () {
            return {
                keyWord: '',
                timer: null,
                list: []
            }
        },
        props: {
            cities: Object
        },

        mounted () {
            this.scroll = new BScroll(this.$refs.scrollView)
        },

        computed: {
            hasNoData () {
                return !this.list.length
            }
        },

        watch: {
            keyWord () {
                if(this.timer) {
                    clearTimeout(this.timer)
                }
                if(!this.keyWord) {
                    this.list = []
                    return
                }
                this.timer = setTimeout(() => {
                    const result = []
                    for (let key in this.cities) {
                        this.cities[key].forEach(item => {
                            if(item.name.indexOf(this.keyWord) > -1 ||
                            item.spell.indexOf(this.keyWord) > -1) {
                                result.push(item)
                            }
                        });
                    }
                    this.list = result
                }, 100)
            }
        },

        methods: {
            changeCity (city) {
                this.keyWord = ''
                this.$store.commit('changeCity', city)
                this.$router.push('/')
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl';
    .search
        height .72rem
        padding 0 .1rem
        background-color $bgColor
        .search-input
            color #666
            width 100%
            height .62rem
            line-height .62rem
            box-sizing border-box
            text-align: center
            padding 0 .1rem
            border-radius .06rem
    .search-content
        overflow hidden
        z-index 1
        position absolute
        top 1.58rem
        right 0
        left 0
        bottom 0
        background #eee
        .search-item
            line-height .63rem
            padding .2rem
            color #666 
            background-color #fff
</style>
