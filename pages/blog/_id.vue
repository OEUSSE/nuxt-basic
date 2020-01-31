<template>
    <div class="container">
        <div class="card">
            <div class="card-body">
                <h1>{{ post.title }}</h1>
                <p>{{ post.body }}</p>
                <p class="small">{{ post.author }}</p>
                <nuxt-link v-if="post.title" to="/blog" class="btn btn-primary">Atras</nuxt-link>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'

export default {
    head: {
        title: `Blog - Artículo`
    },
    data() {
        return {}
    },
    async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
        try {
            let post = {}
            let author = {}
            
            const postResponse = await axios.get(`https://jsonplaceholder.typicode.com/posts/${params.id}`)
            post = postResponse.data

            const userId = postResponse.data.userId

            const authorResponse = await axios.get(`https://jsonplaceholder.typicode.com/users/${userId}`)
            author = authorResponse.data

            post.author = author.name

            return { post, author }
        } catch (error) {
            console.error(error)
            return { error }
        }
    }
}
</script>
