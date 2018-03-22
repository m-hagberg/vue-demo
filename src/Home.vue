<template lang='pug'>
.frontpage(style={'height': '100vh'})
    .content
        .thumbnails(style={'margin-top': '5rem'})
            .box-card(v-for='slideshow in slideshows')
                router-link(:to='slideshow.infos.path' @click.native="click")
                    .embedded-slideshow-container
                        component(:is="slideshow", :embedded='true',
                                :keyboardNavigation='false',
                                :mouseNavigation='false')
                    .caption
                    h3 {{slideshow.infos.title}}
                    p.thumbnail-description {{slideshow.infos.description}}

        h1
            span(style={'font-size': '4rem'}) Presentation made with
            span.logo
            span Eagle
            span.grey .js
            span(style={'font-size': '4rem', 'display': 'block'}) A slideshow framework for hackers
</template>

<script>
import slideshows from 'slideshows/slideshows'

export default {
    data: function () {
        return {
            slideshows: slideshows.list
        }
    },
    mounted: function () {
        console.log(this.slideshows)
        document.currentSlide = {}
    },
    methods: {
        click: function (evt) {
            evt.stopPropagation()
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
@import "node_modules/eagle.js/src/themes/frontpage/frontpage";
h1 {
    transform: scale(.25);
    position: absolute;
    width: 600px;
    bottom: -5rem;
}
.logo {
    display: inline-block;
    width: 130px;
    height:90px;
    margin-right: 0.1em;
    background-image: url(./logo.svg);
    background-size: contain;
    background-position: center bottom;
    background-repeat: no-repeat;
}

.github-star {
    display: block;
    margin: 0 auto;
    margin-top: -10px;
}
</style>
