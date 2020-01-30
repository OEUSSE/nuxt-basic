<template>
    <div class="container mt-5">
        <div class="row">
            <h1>Blog</h1>
        </div>
        <div class="row">
            <div class="col-md-3" v-for="(article, index) in articles" :key="index">
                <h2>
                    <nuxt-link :to="`/blog/${article.id}`">{{ article.text }}</nuxt-link>
                </h2>                
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'blog',
    head: {
        title: 'Blog'
    },
    data() {
        return {
            articles: [
                { id: 1, text: 'Titulo #1' },
                { id: 2, text: 'Titulo #2' },
                { id: 3, text: 'Titulo #3' },
                { id: 4, text: 'Titulo #4' },
            ]
        }
    }
}
</script>
