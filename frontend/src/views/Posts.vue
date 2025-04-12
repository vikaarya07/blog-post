<template>
    <div class="mx-auto p-5 lg:px-14 pt-28">
        <h1 class="text-3xl font-bold mb-6">Blog Posts</h1>

        <!-- Loading state -->
        <div v-if="loading" class="text-gray-500">Loading posts...</div>

        <!-- Empty state -->
        <div v-else-if="posts.length === 0" class="text-gray-500">No posts available.</div>

        <!-- Grid Posts -->
        <div v-else class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-6">
            <div v-for="post in posts" :key="post.id"
                class="bg-white border border-slate-300 p-4 rounded-lg hover:shadow transition h-full flex flex-col">
                <router-link :to="`/post/${post.id}`" class="flex flex-col flex-grow">
                    <h2 class="text-lg font-semibold mb-2">{{ post.title }}</h2>
                    <p class="text-gray-700 flex-grow">
                        {{ post.content.slice(0, 100) }}<span v-if="post.content.length > 100">...</span>
                    </p>
                </router-link>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import api from '../api'

const posts = ref([])
const loading = ref(true)

const fetchPosts = async () => {
    try {
        const res = await api.get('/posts')
        posts.value = res.data
    } catch (error) {
        console.error('Gagal fetch posts:', error)
    } finally {
        loading.value = false
    }
}

onMounted(fetchPosts)
</script>