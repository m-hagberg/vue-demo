<template lang="pug">
#MyFirstSlideshow.eg-theme-agrume
    .eg-slideshow
        v-slide
            h2 Vue.js - an introduction
            eg-transition(enter="flipInY")
                img(src="/static/vue-logo.png" style={'display': 'block', 'margin': '0 auto'})

        slide(:steps=2 enter="bounceInRight" leave="bounceOutLeft")
            h3 What is Vue?
            eg-transition(enter="fadeIn")
                ul(v-if="step >= 2")
                    li Started in late 2013, first release in Feb 2014
                    li Open-source progressive JS framework for building user interfaces
                    li Created by ex-Google employee
                        em  Evan You
                    li
                        |Vue; pronounced
                        tt /vjuː/
                        |&ndash; like
                        em “view”

        v-slide(:steps=2)
            eg-modal
                h2 Less opinionated
                small As such, it tends to be easier for developers to pick up
                eg-transition(enter="bounceInUp")
                    img(src="/static/tweet.png" style={'display': 'block', 'margin': '5rem auto'} v-if="step >= 2")

        v-slide(:steps=2)
            h4 Who is using it?
            sub
                eg-transition(enter="fadeIn")
                    ul(v-if="step >= 2")
                        li Alibaba
                        li Baidu
                        li Weex
                        li Xiaomi
                        li Expedia
                        li Nintendo
                        li Sainsbury's
                        li Monito
                        li GitLab
                        li ZenMate
                        li Codeship
                        li Adobe
                        li IBM
                        li and more...

        v-slide(:steps=3)
            h3 Getting started

            div(v-if="step >= 2")
                eg-code-block(lang="bash").
                    $ npm i -g vue-cli
                    $ vue init webpack

            div(v-if="step >= 3")
                eg-code-block(lang="javascript").
                    const app = new Vue({ ... })

        v-slide
            h4
            eg-code-block(lang="html").
                &lt;div id="msg"&gt;{{ message }}&lt;/div&gt;

            eg-code-block(lang="javascript").
                const data = {
                    message: 'Hello'
                };

                // Instantiate Vue on the element
                new Vue({
                    el: '#msg',
                    data: data
                });

                // Getters and setters are now proxied,
                // so we can do this
                data.message = 'Hi';

        v-slide
            eg-modal
                h5 Directives

                div(style={'max-width': '90vw', 'margin': '0 auto'})
                    em v-bind
                    eg-code-block(lang="html").
                        &lt;!-- full syntax --&gt;
                        &lt;a v-bind:href="url"&gt;&lt;/a&gt;

                        &lt;!-- shorthand --&gt;
                        &lt;a :href="url"&gt;&lt;/a&gt;

                    em v-on
                    eg-code-block(lang="html").
                        &lt;!-- full syntax --&gt;
                        &lt;a v-on:click="doSomething"&gt;&lt;/a&gt;

                        &lt;!-- shorthand --&gt;
                        &lt;a @click="doSomething"&gt;&lt;/a&gt;

        v-slide
            eg-modal
                h5 Binding HTML classes

                div(style={'max-width': '90vw', 'margin': '0 auto'})
                    eg-code-block(lang="html").
                        &lt;div :class="{
                            'active': isActive,
                            'text-danger': hasError
                        }"&gt;&lt;/div&gt;

                    eg-code-block(lang="javascript").
                        data: {
                            isActive: true,
                            hasError: false
                        }

</template>

<script>
import eagle from 'eagle.js'

const TransitionedSlide = {
    mixins: [eagle.slide],
    props: {
        enter: {default: 'bounceInRight'},
        leave: {default: 'bounceOutLeft'}
    }
}

export default {
    mixins: [ eagle.slideshow ],
    infos: {
        title: 'A Vue.js introduction',
        description: 'iStone, April 9th, 2018',
        path: 'vue-presentation'
    },
    components: {
        'v-slide': TransitionedSlide
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
    .eg-code-block {
        margin-bottom: 3rem;
    }
    h2,
    h4 {
        margin-bottom: 1rem;
    }
    p,
    small,
    h5 {
        text-align: center;
        display: block;
    }
    small {
        font-size: 1.5rem;
    }
    p,
    li {
        font-family: 'Raleway';
    }
    li {
        line-height: 2;
    }
    sub {
        font-size: 1.5rem;
    }
    .eg-slide-content {
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
    }
}
</style>
