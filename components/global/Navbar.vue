<template>
    <div class="navbar">
        <div class="wrapper">
            <div class="desktop" v-if="!isMobile">
				<nuxt-link to="/" class="brand_logo">Movie Blog</nuxt-link>
				<ul class="nav_items">
                    <li><nuxt-link to="/">Home</nuxt-link></li>
				</ul>
			</div>
        </div>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                isMobile: false
            }
        }
    }
</script>
<style lang="stylus">
    .navbar
        position: fixed
        top: 0
        left: 0
        right: 0
        width: 100%
        z-index: 7
        transition: .3s
        opacity: 1
        backdrop-filter: blur(10px)
        background-color: #0000003b
        .brand_logo
            font-family: 'bebas-bold'
            font-weight: bold
            font-size: 24px
            color: #e40a14
            letter-spacing: 5px
        .desktop
            display: flex
            justify-content: space-between
            align-items: center
            padding: 15px 50px
        .mobile
            display: flex
            align-items: center
            justify-content: space-between
            padding: 20px
            color: #e40a14
            .burger
                .line
                    width: 25px
                    height: 2px
                    display: block
                    border-radius: 2px
                    background-color: #fff
                    &.middle
                        margin: 5px 0
        .nav_items
            display: flex
            align-items: center
            li
                margin: 0 16px
                padding: 5px 10px
                a
                    font-family: 'bebas-bold'
                    font-weight: bold
                    font-size: 18px
                    color: white
</style>