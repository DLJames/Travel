<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <div class="iconfont back-icon">&#xe624;</div>
        </router-link>
    </div>
</template>

<script>
    export default {
        name: 'City',
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl';
    .header
        position relative
        height $headerHeight
        line-height $headerHeight
        color #fff
        text-align center 
        font-size .32rem
        overflow hidden
        background-color $bgColor
        .back-icon
            position absolute
            top 0
            left 0
            color #fff
            width .64rem
            text-align: center
            font-size: .4rem
</style>
