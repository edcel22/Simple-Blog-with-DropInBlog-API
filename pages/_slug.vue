<template>
    <div class="inner_page">
        <Banner :bannerImage="res.post.featuredImage" :title="res.headTitle" :description="res.headDescription" />
        <div class="page_wrapper">
            <div class="extra_text">Published Date: {{ res.post.publishedAt }}</div>
            <div class="extra_text">Read Time: {{ res.post.readtime }}</div>
            <section class="authors">
                <div class="section_header">
                    <h3 class="section_title">Author</h3>
                </div>
                <div class="section_content">
                    <div class="author">
                        <img :src="res.post.author.photo" alt="">
                        <div class="name">{{ res.post.author.name }}</div>
                    </div>
                </div>
            </section>
            <section class="post_content" v-html="res.post.content"></section>
        </div>
    </div>
</template>
<script>
    import { mapGetters, mapMutations } from 'vuex'

    export default {
        components: {
            Banner: () => import('~/components/global/Banner'),
        },
        data () {
            return {
                res: '',
            }
        },
        asyncData({$axios, params}) {
            return $axios.get(`https://api.dropinblog.com/v1/json/post/?b=${process.env.DIB_ID}&post=${params.slug}`).then( res => {
                return {
                    res: res.data.data
                }
            })
        },
        head () {
            let host = process.env.BASE_URL
            let me = this

            return {
                title: `${me.res.headTitle} | Movie Blog`,
                link: [
                    {
                        rel: 'canonical',
                        href: `${host}${this.$route.fullPath}`
                    }
                ],
                meta: [
                    { hid: 'og:title', property: 'og:title', content: `${me.res.headTitle} | Movie Blog` },
                ]
            }
        }
        
    }
</script> 
<style lang="stylus">
   .inner_page  
        height: 100%
        min-height: 852px
        .extra_text
            font-family: 'bebas-bold'
            font-size: 16px
            color: white
            margin-bottom: 15px
        section
            .section_header
                display: flex
                justify-content: space-between
                align-items: center
                font-family: 'bebas-bold'
                margin-bottom: 30px
                h3
                    color: white
                    font-size: 34px
            .section_content
                display: flex;
                flex-flow: row wrap;
                .author
                    width: 100%
                    flex: 0 0 calc(20% - 20px)
                    margin: 0 10px 20px
                    overflow: hidden
                    img
                        width: 80px
                        height: 80px
                        border-radius: 50%
                        overflow: hidden
                        object-fit: cover
                        object-position: top 
                    .name
                        font-family: 'bebas-bold'
                        font-size: 16px
                        color: white
                    .name
                        padding: 10px 0
            &.post_content
                a, h1, h2, h3, h4, h5, p, span
                    color: white
                    font-family: 'bebas-bold'
                    color: white
                    padding: 5px
</style>