<template lang="pug">
#MyFirstSlideshow.eg-theme-agrume
    .eg-slideshow
        slide(enter="bounceInTop" leave="bounceOutLeft")
            h2 Vue.js - an introduction
            eg-transition(enter="flipInY")
                img(src="/static/vue-logo.png" style={'display': 'block', 'margin': '0 auto'})

        slide(:steps=6 enter="bounceInRight" leave="bounceOutLeft")
            h3 Short history
            eg-transition(leave="bounceOutLeft")
                ul(v-if="step <= 6")
                    eg-transition(enter="flipInX")
                        li(v-if="step >= 2") Started in late 2013, first release in Feb 2014
                    eg-transition(enter="flipInX")
                        li(v-if="step >= 3") Open-source progressive framework for building UI
                    eg-transition(enter="flipInX")
                        li(v-if="step >= 4") Created by ex-Google employee
                            strong  Evan You
                    eg-transition(enter="flipInX")
                        li(v-if="step >= 5")
                            |Vue; pronounced
                            tt  /vjuː/
                            |&ndash; like
                            em “view”
                    eg-transition(enter="flipInX")
                        li(v-if="step >= 6") Designed to be incrementally adoptable
        slide(:steps=2 enter="bounceInRight" leave="bounceOutLeft")
            h3 What is Vue?
            ul(v-if="step >= 2")
                eg-transition(enter="bounceInRight")
                    li HTML-based template syntax

        slide(enter="bounceInRight" leave="bounceOutLeft")
            h3 Want cool effects?
            p.
                Code your own, or try stealing for the other slideshows!
</template>

<script>
import eagle from 'eagle.js'
export default {
    mixins: [ eagle.slideshow ],
    infos: {
        title: 'A Vue.js introduction',
        description: 'iStone, April 9th, 2018',
        path: 'vue-presentation'
    }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Raleway);
@import '~eagle.js/src/themes/agrume/agrume';

#MyFirstSlideshow {
    .eg-slideshow {
        font-family: 'Raleway';
        background-color: #fff;

        .eg-slide {
            .eg-slide-content {
                width: 25em;
                max-width: 80%;
                margin: 0 auto;
            }
        }
    }
    p,
    li {
        font-family: 'Raleway';
    }
    li {
        line-height: 2;
    }
    .eg-slide-content {
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
    }
}
</style>
