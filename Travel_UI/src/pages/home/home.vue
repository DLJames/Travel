<template>
    <div>
        <home-header></home-header>
        <home-swiper :swiper-list="swiperList"></home-swiper>
        <home-icons :icon-list="iconList"></home-icons>
        <home-recommend :recomend-list="recomendList"></home-recommend>
        <home-weekend :weekend-list="weekendList"></home-weekend>
    </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'

export default {
    name: 'home',
    data () {
        return {
            iconList: [],
            swiperList: [],
            recomendList: [],
            weekendList: []
        }
    },
    components: {
        HomeHeader,
        HomeSwiper,
        HomeIcons,
        HomeRecommend,
        HomeWeekend
    },

    mounted () {
        this.getHomeInfo()
    },

    methods: {
        getHomeInfo () {
            axios.get('/api/index.json')
                .then(this.getHomeInfoSucc)
        },

        getHomeInfoSucc (res) {
            let _res = res.data;
            if(!_res.errorCode && _res.data) {
                const data = _res.data;

                this.swiperList = data.swiperList;
                this.iconList = data.iconList;
                this.recomendList = data.recomendList;
                this.weekendList = data.weekendList;
            }
        }
    }
}
</script>

<style scoped>
</style>
 