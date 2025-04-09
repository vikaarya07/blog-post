<template>
    <div>
        <form @submit.prevent="createPost" class="mb-6">
            <input v-model="newPost.title" placeholder="Title" class="border p-2 mb-2 w-full" />
            <textarea v-model="newPost.content" placeholder="Content" class="border p-2 mb-2 w-full"></textarea>
            <button class="bg-blue-500 text-white px-4 py-2 rounded">Add Post</button>
        </form>

        <div v-for="post in posts" :key="post.id" class="mb-4 border p-4 rounded">
            <h2 class="text-xl font-semibold">{{ post.title }}</h2>
            <p class="text-gray-700">{{ post.content }}</p>
            <button @click="deletePost(post.id)" class="text-red-600 text-sm mt-2">Delete</button>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import api from '../api'

const posts = ref([])
const newPost = ref({
    title: '',
    content: ''
})

const fetchPosts = async () => {
    try {
        const res = await api.get('/posts')
        posts.value = res.data
    } catch (error) {
        console.error('Gagal fetch posts:', error)
    }
}


const createPost = async () => {
    if (!newPost.value.title || !newPost.value.content) return
    try {
        await api.post('/posts', newPost.value)
        newPost.value = { title: '', content: '' }
        fetchPosts()
    } catch (error) {
        console.error('Gagal create post:', error)
    }
}

const deletePost = async (id) => {
    try {
        await api.delete(`/posts/${id}`)
        fetchPosts()
    } catch (error) {
        console.error('Gagal delete post:', error)
    }
}


onMounted(fetchPosts)
</script>