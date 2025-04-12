<template>
    <header class="fixed top-0 left-0 w-full z-50 bg-sky-400 p-5 lg:px-14 shadow-md">
        <div class="flex justify-between items-center">
            <span class="text-2xl font-bold text-white">Your Company</span>

            <!-- Hamburger (mobile) -->
            <button class="md:hidden text-white" @click="isOpen = !isOpen">
                <svg v-if="!isOpen" xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8h16M4 16h16" />
                </svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
            </button>

            <!-- Desktop nav -->
            <nav class="hidden md:flex space-x-4 text-base font-semibold text-slate-800">
                <RouterLink to="/" v-slot="{ isActive }">
                    <span :class="navLinkClass(isActive)">Home</span>
                </RouterLink>
                <RouterLink to="/about" v-slot="{ isActive }">
                    <span :class="navLinkClass(isActive)">About</span>
                </RouterLink>
                <RouterLink to="/posts" v-slot="{ isActive }">
                    <span :class="navLinkClass(isActive)">Blog</span>
                </RouterLink>
                <RouterLink to="/contact" v-slot="{ isActive }">
                    <span :class="navLinkClass(isActive)">Contact</span>
                </RouterLink>
            </nav>
        </div>

        <!-- Mobile nav -->
        <nav v-if="isOpen"
            class="md:hidden absolute left-0 top-full w-full bg-sky-400 z-50 p-5 space-y-2 text-base font-semibold text-slate-800 shadow-lg">
            <RouterLink to="/" v-slot="{ isActive }" @click="isOpen = false">
                <div :class="navLinkClass(isActive)">Home</div>
            </RouterLink>
            <RouterLink to="/about" v-slot="{ isActive }" @click="isOpen = false">
                <div :class="navLinkClass(isActive)">About</div>
            </RouterLink>
            <RouterLink to="/posts" v-slot="{ isActive }" @click="isOpen = false">
                <div :class="navLinkClass(isActive)">Blog</div>
            </RouterLink>
            <RouterLink to="/contact" v-slot="{ isActive }" @click="isOpen = false">
                <div :class="navLinkClass(isActive)">Contact</div>
            </RouterLink>
        </nav>
    </header>
</template>

<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const isOpen = ref(false)

function navLinkClass(isActive) {
    return [
        'block px-3 py-1.5 rounded-md transition-all duration-200',
        isActive
            ? 'bg-slate-100 text-slate-800'
            : 'text-white hover:text-slate-800 hover:bg-slate-100'
    ]
}
</script>