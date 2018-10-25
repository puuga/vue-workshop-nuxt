<template>
    <div class="container">
        <WebHeader/>
        <nuxt/>
    </div>
</template>

<script>
import WebHeader from '../components/WebHeader'

export default {
    name: 'blog',
    components: {
        WebHeader
    }
}
</script>

<style scoped>
.container {
    margin: 1rem;
}
</style>
