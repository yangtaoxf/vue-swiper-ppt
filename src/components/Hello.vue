<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .container-box {
        display: flex;
        justify-content: center;
    }
    .container {
        min-width: 800px;
    }
</style>
<template>
    <div class="container-box">
        <div class="container">
            <h1>{{ msg }}</h1>
            <swiper :images="images"></swiper>
        </div>
    </div>

</template>

<script>
import Swiper from './swiper.vue'

export default {
    name: 'hello',
    data () {
        return {
        msg: 'Welcome to Vue-swiper-ppt',
        images: [
            "http://i4.bvimg.com/600318/dc9b2751fb7e091a.png",
            "http://i4.bvimg.com/600318/e98d311c8df5136a.png",
            "http://i4.bvimg.com/600318/c0546ad617bd4684.png",
            "http://i4.bvimg.com/600318/38c5096a1374aa0e.png",
            "http://i1.bvimg.com/600318/09bac0754e72ce98.png",
            "http://i1.bvimg.com/600318/3331fb4c1ef78e94.png",
            "http://i1.bvimg.com/600318/3498177c5d6a2e24.png",
        ],
    }
    },
    components: {
        Swiper
    },
    created() {

    },
}
</script>

