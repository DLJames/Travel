<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{city}}
                <span class="iconfont arrow-icon">&#xe6aa;</span>
            </div>
        </router-link>
    </div>
</template>
<script>
import {mapState} from 'vuex'

export default {
  name: "HomeHeader",

  computed: {
    //   city () {
    //       return this.$store.state.city
    //   }
    ...mapState(['city'])
  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header
    line-height: $headerHeight
    color: #fff
    background-color: $bgColor
    display: flex
    .header-left
        width: .64rem
        .back-icon
            text-align: center
            font-size: .4rem
    .header-right
        // width: 1.24rem
        padding: 0 .1rem
        text-align:center
        color #fff
        .arrow-icon
            font-size: .24rem
            margin-left: -.04rem
    .header-input 
        flex: 1
        height: .64rem
        line-height: .64rem
        color: #ccc
        background: #fff
        border-radius: .1rem
        margin-top: .12rem
        margin-left .12rem
        padding-left: .12rem
</style>
 