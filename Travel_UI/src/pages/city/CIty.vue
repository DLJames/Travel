<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="change"></city-alphabet>
    </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'

    export default {
        name: 'City',

        data () {
            return {
                cities: {},
                hotCities: [],
                letter: ''
            }
        },

        components: {
            CityHeader,
            CitySearch,
            CityList,
            CityAlphabet
        },

        mounted () {
            this.getCityInfo()
        },

        methods: {
            change (letter) {
                this.letter = letter;
            },

            getCityInfo () {
                axios.get('/api/city.json')
                    .then(this.handleSucc)
            },

            handleSucc (res) {
                res = res.data
                if(res.ret && res.data) {
                    const data = res.data

                    this.cities = data.cities
                    this.hotCities = data.hotCities
                }
            }
        }
    }
</script>

<style lang="stylus" scoped>

</style>
