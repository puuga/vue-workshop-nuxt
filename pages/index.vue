<template>
    <section class="container">
        <div v-for="post in posts" :key="post.id" class="post-item">
            <p class="title">
                <strong>
                    <nuxt-link :to="'/content/' + post.id">{{ post.title.rendered }}</nuxt-link>
                </strong>
            </p>

            <p v-html="post.excerpt.rendered">
            </p>
        </div>
    </section>
</template>

<script>

export default {
    layout: 'blog',
    data () {
        return {
            posts: []
        }
    },
    // async mounted () {
    //     this.posts = await this.$axios.$get('https://blog.skooldio.com/wp-json/wp/v2/posts')
    // },
    async asyncData ({app}) {
        return {
            posts: await app.$axios.$get('https://blog.skooldio.com/wp-json/wp/v2/posts')
        }
    }
}
</script>

<style scoped>

.container {
    margin: 1rem;
    min-height: 100vh;
}

.title {
    font-size: 2rem;
}

.post-item {
    background-color: lightgray;
    padding: 1rem;
    margin: 1rem;
    border: 1px solid gray;
    border-radius: 5px;
}

</style>
