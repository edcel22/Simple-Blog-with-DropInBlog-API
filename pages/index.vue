<template>
	<div id="home">
    <Banner :bannerImage="banner_image" :title="banner_title" :description="banner_description" />
    <div class="content">
      <div class="page_wrapper">
        <Category v-for="(category, key) in categories" :category="category" :key="key" />
      </div>
    </div>
  </div>
</template>
<script>
    export default {
      components: {
          Banner: () => import('~/components/global/Banner'),
          Category: () => import('~/components/home/Category'),
      },
      data () {
          return {
              counter: 10,
              categories: [],
              banner_image: '/images/home/banner_large.jpeg',
              banner_title: 'Unlimited Pirated Movies',
              banner_description: 'Read movie informations.'
          }
      },
      methods: {
        getData () {
          this.$axios.get(`/categories?b=${process.env.DIB_ID}`).then( res => {
            this.categories = res.data.data
          }).catch(err => {
            console.log(err)
          })
        }
      },
      mounted () {
        this.getData()
      },
      head () {
        let host = process.env.BASE_URL
        let me = this

        return {
            title: `Home | Movie Blog`,
            link: [
                {
                    rel: 'canonical',
                    href: `${host}${this.$route.fullPath}`
                }
            ],
            meta: [
                { hid: 'og:title', property: 'og:title', content: `Home | Movie Blog` },
            ]
        }
      }
    }
</script> 
