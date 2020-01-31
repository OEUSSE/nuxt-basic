<template>
    <div class="container mt-5">
        <div class="row">
            <div class="card my-2" v-for="post in posts" :key="post.id">
                <div class="card-body">
                    <nuxt-link :to="`/blog/${post.id}`">
                        <h3>{{ post.title }}</h3>
                    </nuxt-link>
                    <p>{{ post.body }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'

export default {
    name: 'blog',
    head: {
        title: 'Blog'
    },
    data() {
        return {
            posts: []
        }
    },
    created() {
        this.getPosts()
    },
    methods: {
        async getPosts() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
                if (response.status === 200) {
                    this.posts = response.data
                }
            } catch (error) {
                console.error(error)
            }
        }
    }
}
</script>
