<template lang="pug">
#MyFirstSlideshow.eg-theme-agrume
    .eg-slideshow
        slide(enter="bounceInLeft" leave="bounceOutLeft")
            h1 Vue.js

        slide(enter="bounceInRight" leave="bounceOutLeft")
            h3 Hey modify me !
            p.
                Come on modify me ! If you are running the development server,
                you will see the changes take effect immediately

        slide(enter="fadeIn")
            h3 Want cool effects?
            p.
                Code your own, or try stealing for the other slideshows !
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
    .eg-slide-content {
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
    }
}
</style>
