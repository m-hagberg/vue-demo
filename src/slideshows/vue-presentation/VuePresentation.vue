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
                    ul(v-if="step >= 2" style={'columns': '3', 'list-style-position': 'inside'})
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

            eg-transition(enter="fadeIn")
                div(v-if="step >= 2")
                    eg-code-block(lang="bash").
                        $ npm i -g vue-cli
                        $ vue init webpack

            eg-transition(enter="fadeIn")
                div(v-if="step >= 3")
                    eg-code-block(lang="javascript").
                        // Using the Vue constructor function
                        const myApp = new Vue({ ... })

        v-slide
            h4
            eg-code-block(lang="html").
                &lt;div id="msg"&gt;{{ message }&shy;}&lt;/div&gt;

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

                .fw-slide
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

                .fw-slide
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
        v-slide(:steps="2" :mouseNavigation="false")
            eg-modal
                h5
                    |Two-way data binding with
                    tt.invert v-model
                twowayBinding
                eg-transition(enter="fadeIn")
                    .fw-slide(style={'margin-top': '2rem'} v-if="step >= 2")
                        eg-code-block(lang="html").
                            &lt;input v-model="boundValue"&gt;
                            &lt;p&gt;{{boundValue}&shy;}&lt;/p&gt;
        v-slide
            eg-modal
                h5 Conditional rendering

                .fw-slide
                    eg-code-block(lang="html").
                        &lt;!-- Using conditional directives as attributes --&gt;
                        &lt;div v-if="type === 'A'"&gt;
                            Type A
                        &lt;/div&gt;
                        &lt;div v-else-if="type === 'B'"&gt;
                            Type B
                        &lt;/div&gt;
                        &lt;div v-else-if="type === 'C'"&gt;
                            Type C
                        &lt;/div&gt;
                        &lt;div v-else&gt;
                            Neither A/B/C
                        &lt;/div&gt;

        v-slide
            eg-modal
                h5 Loops

                .fw-slide
                    eg-code-block(lang="html").
                        &lt;ul id="list"&gt;
                            &lt;li v-for="(item, index) in items"&gt;
                                {&shy;{ index }} - {&shy;{ parentMessage }} {&shy;{ item.message }}
                            &lt;/li&gt;
                        &lt;/ul&gt;

                    eg-code-block(lang="javascript").
                        new Vue({
                            el: '#list',
                            data: {
                                parentMessage: 'Parent',
                                items: [
                                    { message: 'Foo' },
                                    { message: 'Bar' }
                                ]
                            }
                        })

                        /*  Outputs list containing all items in 'items':
                            0 - Parent Foo
                            1 - Parent Bar
                        */

        v-slide
            eg-modal
                h5 Event &amp; key modifiers

                .fw-slide
                    eg-code-block(lang="html").
                        &lt;!-- the click event's propagation will be stopped --&gt;
                        &lt;a v-on:click.stop="oThis"&gt;&lt;/a&gt;

                        &lt;!-- submit event will not reload the page - like evt.preventDefault() --&gt;
                        &lt;form @submit.prevent="onSubmit"&gt;&lt;/form&gt;

                        &lt;!-- modifiers can be chained --&gt;
                        &lt;a @click.stop.prevent="doThat"&gt;&lt;/a&gt;

                        &lt;!-- keycodes are also available - .tab, .delete, .esc, .space, ...--&gt;
                        &lt;input @keyup.enter="submit"&gt;

        slide(:steps=3 enter="bounceInUp" leave="bounceOutUp" :mouseNavigation="false")
            eg-modal
                h5 Components
                buttonclicked
                eg-transition(enter="fadeIn")
                    .fw-slide(style={'margin-top': '2rem'} v-if="step >= 2")
                        eg-code-block(lang="html").
                            &lt;div id="btn"&gt;
                                &lt;buttonclicked&gt;&lt;/buttonclicked&gt;
                            &lt;/div&gt;
                eg-transition(enter="fadeIn")
                    .fw-slide(style={'margin-top': '2rem'} v-if="step >= 3")
                        eg-code-block(lang="javascript").
                            Vue.component('buttonclicked', {
                                props: 'initial_count',
                                data: function() {
                                    return { 'count': 0 }
                                },
                                template: ' &lt;button @click.prevent="countClicks"&gt;
                                                Clicked {{ count }&shy;} times
                                            &lt;/button&gt;',
                                methods: {
                                    'countClicks': function() {
                                        this.count = this.count + 1
                                    }
                                },
                                mounted: function() {
                                    this.number.count = this.initial_count
                                }
                            })

                            new Vue({
                                el: '#btn',
                            })

        slide(:steps="2" enter="bounceInUp" leave="bounceOutUp")
            eg-modal
                h5 Simple SPA routing
                .fw-slide(v-if="step >= 1" style={'font-size': '1.75rem'})
                    p(style={'text-align': 'left'}) Using VueRouter, we want to:
                    ol
                        li
                            |Set a frontend route at
                            tt.invert example.com/user/&lt;id&gt;
                        li Render a "User" component at the route
                        li
                            |Allow the "User" component to pass in the
                            tt.invert &lt;id&gt;
                            |using the
                            tt.invert $route
                            |object's params key:
                            tt.invert $route.params.id
                        li
                            |Render the routes and instantiate app in an
                            tt.invert #app
                            |element
                eg-transition(enter="fadeIn")
                    .fw-slide(v-if="step >= 2" style={'font-size': '1.75rem'})
                        p(style={'text-align': 'left'}) How it's done:
                        .col-2
                            eg-code-block(lang="javascript").
                                const myUserComponent = {
                                    template: '&lt;p&gt;User {{ $route.params.id }&shy;}&lt;/p&gt;'
                                }

                                const router = new VueRouter({
                                    routes: [
                                        { path: '/user/:id', component: myUserComponent }
                                    ]
                                })
                            eg-code-block(lang="html").
                                &lt;div id="app"&gt;
                                    &lt;router-view&gt;&lt;/router-view&gt;
                                &lt;/div&gt;

        v-slide
            h3 And much more...
            sub
                ul
                    li Single-file components
                    li Component-scoped CSS
                    li CommonJS modules
                    li Vue Devtools
                    li Built-in transitions
                    li Dynamic &amp; async components
                    li Custom events and directives
                    li Typescript support
                    li Unit testing
                    li State management with Vuex, or even with Redux (!)
                    li Server-side rendering
                    li Tons of open-source plugins, components, and utilities

        v-slide
            h3 Bottom line
            p You should definitely check out Vue if...
            sub
                ul
                    li you like really clean code
                    li you want something flexible and modular
                    li you want the easiest learning curve
                    li you want the most lightweight framework
                    li you want separation of concerns in one file
                    li you are working alone or have a small team
                    li you work with designers and need clean HTML files
                    li you like using templates

        v-slide
            h5 Bonus: 2-minute <em>no-config</em> setup
            eg-code-block(lang="bash")  $ npm i -D poi
            tt index.js
            eg-code-block(lang="javascript").
                import Vue from 'vue'

                new Vue({
                    el: '#app',
                    render() {
                        return <p style="display: inline; font-size: 1.5rem;">&lt;h1&gt;Hello Vue.&lt;/h1&gt;</p>
                    }
                })

        v-slide(:mouseNavigation="false")
            h3 Fin'
            h1 🎉
</template>

<script>
import eagle from 'eagle.js'

const TransitionedSlide = {
    mixins: [eagle.slide],
    data: {
        boundValue: ''
    },
    props: {
        enter: { default: 'bounceInRight' },
        leave: { default: 'bounceOutLeft' }
    }
}

const buttonClicked = {
    props: ['initial_count'],
    data: function () {
        return { 'count': 0 }
    },
    template: '<button @click.prevent="onclick">Clicked {{ count }} times</button>',
    methods: {
        'onclick': function () {
            this.count = this.count + 1
        }
    },
    mounted: function () {
        this.number.count = this.initial_count
    }
}

const twowayBinding = {
    data: function () {
        return { boundValue: 'Data binding' }
    },
    template: '<p><input @keyup="doThings" v-model="boundValue" style="background: #fff" spellcheck="false"> = <span>{{boundValue}}</span></p>',
    methods: {
        'doThings': function () {
            this.boundValue += ' ftw'
        }
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
        'v-slide': TransitionedSlide,
        'buttonclicked': buttonClicked,
        'twowayBinding': twowayBinding
    }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Raleway);
@import url(https://cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/codepen-embed.min.css);
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
    .fw-slide {
        max-width: 90vw;
        margin: 0 auto;
    }
    .eg-slide-content {
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
    }
    button {
        color: #212529;
        background-color: #f8f9fa;
        border-color: #f8f9fa;
        display: block;
        font-weight: 400;
        text-align: center;
        white-space: nowrap;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        border: 1px solid transparent;
        padding: .375rem .75rem;
        font-size: 1rem;
        line-height: 1.5;
        border-radius: .25rem;
        transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
        margin: 0 auto;
    }

    button:hover,
    tt.invert {
        background-color: #e2e6ea;
        border-color: #dae0e5;
    }

    tt.invert {
        color: #212529;
        margin: 0 1rem;
        padding: .25rem 1rem;
        border-radius: 5px;
    }

    .col-2 {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 0 2rem;

        .hljs.box {
            display: inherit;
        }
    }

    .hljs{display:block;overflow-x:auto;padding:0.5em;color:#333;background:#f8f8f8}.hljs-comment,.hljs-quote{color:#998;font-style:italic}.hljs-keyword,.hljs-selector-tag,.hljs-subst{color:#333;font-weight:bold}.hljs-number,.hljs-literal,.hljs-variable,.hljs-template-variable,.hljs-tag .hljs-attr{color:#008080}.hljs-string,.hljs-doctag{color:#d14}.hljs-title,.hljs-section,.hljs-selector-id{color:#900;font-weight:bold}.hljs-subst{font-weight:normal}.hljs-type,.hljs-class .hljs-title{color:#458;font-weight:bold}.hljs-tag,.hljs-name,.hljs-attribute{color:#000080;font-weight:normal}.hljs-regexp,.hljs-link{color:#009926}.hljs-symbol,.hljs-bullet{color:#990073}.hljs-built_in,.hljs-builtin-name{color:#0086b3}.hljs-meta{color:#999;font-weight:bold}.hljs-deletion{background:#fdd}.hljs-addition{background:#dfd}.hljs-emphasis{font-style:italic}.hljs-strong{font-weight:bold}
}
</style>
