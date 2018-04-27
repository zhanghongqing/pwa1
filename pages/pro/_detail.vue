<template>
    <div id="detail">
        页面id {{$route.params.detail}}<br>
        <router-link :to="{
            name: 'proDetail',
            params: {
                detail: $route.params.detail + 'a'
            }
        }">{{$route.params.detail + 'a'}}</router-link>
    </div>
</template>

<script>
    import {mapState} from 'vuex'

    export default {
        name: "pro-_detail",
        async asyncData ({store, route}) {
            await store.dispatch('detail/setWeather', {woeid: 2151849})
        },
        computed: {
            ...mapState('detail', [
                'weather'
            ])
        },
        created () {
            console.log(`Weather of Shanghai: ${this.weather.text}, ${this.weather.temp}`);
        }
    }
</script>

<style lang="stylus" scoped>
    #detail
        background #fafafa
        line-height 100px
        text-align center
</style>
