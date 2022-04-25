<template>
    <div class="items">
        <div class="item" v-for="(movie, index) in movies" data-aos="fade-up" :data-aos-delay="`${100 * index}`" data-aos-once="true">
            <div class="thumbnail">
                <img :src="movie.featuredImage" :alt="movie.seoTitle">
            </div>
            <div class="texts">
                <p class="title">{{ movie.title }}</p>
                <p>Author: {{ movie.author.name }}</p>
                <p>Summary: <br> {{ movie.summary }}</p>
            </div> 
            <nuxt-link :to="`/${movie.slug}`" class="link read_more">Read More</nuxt-link>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            movies: {
                type: Array,
                default: []
            }
        },  
    }
</script> 
<style lang="stylus">
    .items
        display: flex
        flex-flow: row wrap
        align-items: flex-start
        .item
            flex: 0 0 calc(20% - 20px)
            margin: 0 10px 20px
            border-radius: 20px
            overflow: hidden
            font-family: 'bebas-regular'
            background: #181515
            position: relative
            transition: 0.5s
            svg
                position: absolute
                top: 10px
                right: 10px
                cursor: pointer
                transition: .3s
                transform: scale(.8)
                &:hover
                    transform: scale(1)
                    transition: .3s
            .thumbnail
                height: 100%
                overflow: hidden
                position: relative
                .overlay
                    position: absolute
                    top: 0
                    bottom: 0
                    left: 0
                    right: 0
                    width: 100%
                    height: 100%
                    background-color: #000000ad
                    display: flex
                    align-items: flex-end
                    justify-content: center
                    transition: 0.5s
                    opacity: 0
                    .read_more
                        text-decoration: none
                        color: white
                        padding: 10px
                        border-radius: 5px
                        background-color: #c41414
                        margin-bottom: 20px
                &:hover
                    .overlay
                        opacity: 1
                img
                    width: 100%
                    height: 300px
                    object-fit: cover
                    object-position: center
            .texts
                padding: 10px
                color: white
                p
                    margin: 5px 0
            .read_more
                padding: 0 10px 20px
</style>