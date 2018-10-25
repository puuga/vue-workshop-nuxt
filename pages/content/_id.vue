<template>
    <section class="container">
        <div class="content" v-if="post">
            <h1>{{ post.title.rendered }}</h1>
            <p>
                <img :src="post._embedded['wp:featuredmedia'][0].media_details.sizes.medium.source_url" />
            </p>
            <p v-html="post.content.rendered"></p>
        </div>
    </section>
</template>

<script>

export default {
    layout: 'blog',
    head () {
        return {
            title: this.post.title.rendered,
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: this.post.excerpt.rendered
                },
                {
                    property: 'og:image',
                    content: this.post._embedded['wp:featuredmedia'][0].media_details.sizes.medium.source_url
                },
                {
                    property: 'og:description',
                    content: this.post.excerpt.rendered
                }
            ]
        }
    },
    mounted() {
        console.log()
    },
    data () {
        return {
        }
    },
    async mounted () {
        
    },
    async asyncData ({app, route}) {
        console.log('post id', route.params.id);
        return {
            post: await app.$axios.$get('https://blog.skooldio.com/wp-json/wp/v2/posts/' + route.params.id + '?_embed')
        }
    }
}
</script>

<style>

.container {
    margin: 1rem;
    min-height: 100vh;
}

</style>
