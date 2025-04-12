<template>
    <section class="min-h-screen py-16 px-4 sm:px-8 lg:px-24 pt-28">
        <div class="max-w-3xl mx-auto bg-white p-5 border border-slate-300 rounded-lg">
            <h1 class="text-4xl font-bold text-center text-gray-800  mb-8">Contact Me</h1>

            <p class="text-center text-gray-600 mb-12">
                Have a project or just want to say hi? Fill the form below or reach out via email.
            </p>

            <form class="space-y-6">
                <div>
                    <label for="name" class="block text-sm font-medium text-gray-700 mb-1">Name</label>
                    <input type="text" id="name"
                        class="w-full px-4 py-2 border border-gray-300 rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-sky-400"
                        placeholder="Your name" />
                </div>

                <div>
                    <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                    <input type="email" id="email"
                        class="w-full px-4 py-2 border border-gray-300 rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-sky-400"
                        placeholder="you@example.com" />
                </div>

                <div>
                    <label for="message" class="block text-sm font-medium text-gray-700 mb-1">Message</label>
                    <textarea id="message" rows="5"
                        class="w-full px-4 py-2 border border-gray-300 rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-sky-400"
                        placeholder="Tell me about your project..."></textarea>
                </div>

                <div class="text-center">
                    <button type="submit"
                        class="inline-block px-6 py-2 bg-sky-500 hover:bg-sky-600 text-white font-semibold rounded-lg transition duration-200">
                        Send Message
                    </button>
                </div>
            </form>
        </div>
    </section>
</template>