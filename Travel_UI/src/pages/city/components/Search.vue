<template>
    <div class="search">
        <input class="search-input" type="text" placeholder="请输入城市名或拼音"/>
    </div>
</template>

<script>
    export default {
        name: 'City',
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
</style>
