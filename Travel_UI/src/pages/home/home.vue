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
import { mapState } from 'vuex'

export default {
    name: 'home',
    data () {
        return {
            lastCity: '',
            iconList: [],
            swiperList: [],
            recomendList: [],
            weekendList: []
        }
    },

    computed: {
        ...mapState(['city'])
    },

    components: {
        HomeHeader,
        HomeSwiper,
        HomeIcons,
        HomeRecommend,
        HomeWeekend
    },

    methods: {
        getHomeInfo () {
            axios.get('/api/index.json?city=' + this.city)
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
    },

    mounted () {
        this.lastCity = this.city;
        this.getHomeInfo()
    },

    activated () {
        if(this.lastCity !== this.city) {
            this.lastCity = this.city;
            this.getHomeInfo()
        }
    }
}
</script>

<style scoped>
</style>
 