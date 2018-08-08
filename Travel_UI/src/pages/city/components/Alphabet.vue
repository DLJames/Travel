<template>
    <ul class="alphabet">
        <li 
            class="item" v-for="item in letters" 
            :key="item" 
            :ref="item"
            @touchstart="handleTouchcStart"
            @touchmove="handleTouchcMove"
            @touchend="handleTouchcEnd"
            @click="hanndleLetterClick"
        >{{item}}</li>
    </ul>
</template>

<script>

    export default {
        name: 'CityAlphabet',
        props: {
            cities: Object
        },
        data () {
            return {
                touchStatus: false,
                startY: 0,
                timer: null
            }
        },
        updated () {
            this.startY = this.$refs['A'][0].offsetTop
        },

        computed: {
            letters () {
                const letters = [];

                for (let key in this.cities) {
                    letters.push(key)
                }
                return letters;
            }
        },
        methods: {
            handleTouchcStart () {
                this.touchStatus = true;
            },
            handleTouchcMove (evt) {
                if(this.touchStatus) {
                    if(this.timer) {
                        clearTimeout(this.timer)
                    }
                    this.timer = setTimeout(() => {
                        let touchY = evt.touches[0].clientY - 79
                        let index = Math.floor((touchY - this.startY) / 20 )
                        if(index >= 0 && index <= this.letters.length) {
                            this.$emit('change', this.letters[index])
                        }
                    }, 16)
                }
            },
            handleTouchcEnd () {
                this.touchStatus = false;
            },
            hanndleLetterClick (event) {
                this.$emit('change', event.target.innerHTML);
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl';
    .alphabet
        position absolute
        top 1.58rem
        right 0
        bottom 0
        width .4rem
        display flex
        justify-content center
        flex-direction column
        .item
            line-height .4rem
            text-align center
            color $bgColor
</style>
