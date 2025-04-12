<template>
    <section class="min-h-screen py-16 px-4 sm:px-8 lg:px-24 pt-28">
        <div class="max-w-4xl mx-auto text-center">
            <h1 class="text-4xl font-bold text-gray-800 mb-6">About Me</h1>
            <p class="text-lg text-gray-600 mb-8">
                Hello! I'm <span class="font-semibold text-blue-600">viksite.com</span>,
                a passionate web developer specializing in building modern web applications using
                <span class="font-medium">Vue.js</span> and <span class="font-medium">Tailwind CSS</span>.
                I love crafting beautiful interfaces and seamless user experiences.
            </p>
            <div class="flex flex-col md:flex-row justify-center items-center gap-8">
                <img src="../assets/profile.png" alt="Your Photo"
                    class="w-48 h-48 rounded-full object-cover border-4 border-blue-500" />
                <div class="text-left max-w-md">
                    <h2 class="text-2xl font-semibold text-gray-800 mb-3">What I Do</h2>
                    <ul class="list-disc pl-5 text-gray-600 space-y-2">
                        <li>Build responsive web apps with Vue 3</li>
                        <li>Style modern UI with Tailwind CSS 4</li>
                        <li>Write clean, maintainable code</li>
                        <li>Integrate REST APIs and backend services</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>
</template>