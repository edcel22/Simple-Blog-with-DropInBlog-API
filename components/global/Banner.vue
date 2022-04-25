<template>
    <div class="banner">
        <img :src="bannerImage" alt="Movie banner" class="banner_image" v-if="bannerImage">
        <div class="main_texts" data-aos="fade-up" data-aos-duration="500" data-aos-once="true">
            <h1 class="title" v-if="title">{{ title }}</h1>
            <p class="label" v-if="description">{{ description }}</p>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            bannerImage: {
                type: String,
                default: '/images/gradient_bg.webp'
            },
            title: {
                type: String,
                default: null
            },
            description: {
                type: String,
                default: null
            }
        }
    }
</script>   
<style lang="stylus" scoped>
    .banner
        position: relative
        width: 100%
        height: 50vh
        background-color: #000
        .banner_image
            width: 100%
            height: 100%
            opacity: 0.3
            object-fit: cover
            object-position: center
        .main_texts
            position: absolute
            top: 50%
            left: 50%
            transform: translate(-50%, -50%)
            text-align: center
            color: white
            .title
                font-family: 'bebas-bold'
                font-size: 60px
                padding-bottom: 20px
                letter-spacing: 5px
            .label
                font-family: 'bebas-regular'
                font-size: 28px
                letter-spacing: 3px
</style>