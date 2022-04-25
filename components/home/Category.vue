<template>
    <section class="genre">
        <div class="section_header">
            <h3 class="section_title">{{ category.title }}</h3>
        </div>
        <Movies :movies="this.movies" />
    </section>
</template>
<script>
    export default {
        components: {
            Movies: () => import('~/components/home/Movies'),
        },
        props: {
            category: {
                type: Object,
                default: null
            }
        },
        data () {
            return {
                movies: [],
            }
        },
        methods: {
            getData () {
                this.$axios.get(`/?b=${process.env.DIB_ID}&featureimage=thumb&category=${this.category.slug}`).then( res => {
                    this.movies = res.data.data.posts
                }).catch(err => {
                    console.log(err)
                })
            }
        },
        mounted () {
            this.getData()
        }
    }
</script> 
<style lang="stylus">
    section
        padding: 30px 0
        .section_header
            display: flex
            justify-content: space-between
            align-items: center
            font-family: 'bebas-bold'
            margin-bottom: 30px
            .section_title
                font-size: 34px
            .show_more
                font-size: 22px
                color: #e40a14
                letter-spacing: 2px
                text-decoration: underline
        &.genre
            display: flex
            flex-flow: column wrap
            color: white
</style>