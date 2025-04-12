<template>
    <article class="max-w-6xl mx-auto p-6 grid grid-cols-1 lg:grid-cols-3 gap-8 pt-28">
        <!-- Main Content -->
        <div class="lg:col-span-2">
            <div v-if="loading" class="text-gray-500">Loading post...</div>
            <div v-else-if="!post" class="text-gray-500">Post not found.</div>

            <div v-else class="border border-slate-300 bg-white p-5 rounded-lg">
                <h1 class="text-3xl font-bold mb-2">{{ post.title }}</h1>
                <p class="text-gray-500 text-sm mb-6">Published on {{ formatDate(post.created_at) }}</p>
                <div class="prose max-w-none text-justify" v-html="post.content"></div>
            </div>
        </div>

        <!-- Aside: Latest Posts -->
        <aside>
            <h2 class="text-xl font-semibold mb-4">Latest Posts</h2>
            <ul class="space-y-2">
                <li v-for="item in latestPosts" :key="item.id">
                    <router-link :to="`/post/${item.id}`"
                        class="block border border-slate-300 rounded-lg p-3 hover:bg-gray-50 transition bg-white">
                        <div class="font-medium">{{ item.title }}</div>
                        <div class="text-gray-400 text-xs">{{ formatDate(item.created_at) }}</div>
                    </router-link>
                </li>
            </ul>
        </aside>

    </article>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import api from '../api'

const post = ref(null)
const loading = ref(true)
const latestPosts = ref([])

const route = useRoute()
const postId = route.params.id

const fetchPost = async () => {
    try {
        const res = await api.get(`/posts/${postId}`)
        post.value = res.data
    } catch (error) {
        console.error('Gagal fetch post:', error)
    } finally {
        loading.value = false
    }
}

const fetchLatestPosts = async () => {
    try {
        const res = await api.get(`/posts?limit=5`) // Sesuaikan dengan API kamu
        latestPosts.value = res.data
    } catch (error) {
        console.error('Gagal fetch latest posts:', error)
    }
}

const formatDate = (dateStr) => {
    const options = { year: 'numeric', month: 'long', day: 'numeric' }
    return new Date(dateStr).toLocaleDateString(undefined, options)
}

onMounted(() => {
    fetchPost()
    fetchLatestPosts()
})
</script>
