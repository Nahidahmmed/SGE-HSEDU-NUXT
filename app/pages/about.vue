<script setup lang="ts">
definePageMeta({
    layout: 'default'
})
</script>

<template>
    <main class="min-h-screen">
        <!-- Hero Section -->
        <section class="relative bg-gradient-primary text-white py-20">
            <div class="max-w-7xl mx-auto px-4 text-center">
                <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">
                    About <span class="text-white">SGE-HSEDU</span>
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-slide-up text-black-300">
                    Learn more about our mission and values
                </p>
            </div>
        </section>

        <!-- Content Section -->
        <section class="py-20 bg-black-900">
            <div class="container mx-auto px-4">
                <div class="max-w-4xl mx-auto">
                    <div class="card mb-8">
                        <h2 class="text-3xl font-bold text-white mb-4">Our Mission</h2>
                        <p class="text-black-300 text-lg leading-relaxed">
                            We are dedicated to providing the best educational experience through modern technology and
                            innovative design. Our platform combines the power of Nuxt.js with the beauty of Tailwind
                            CSS to create exceptional user experiences.
                        </p>
                    </div>

                    <div class="card mb-8">
                        <h2 class="text-3xl font-bold text-white mb-4">Our Values</h2>
                        <div class="grid md:grid-cols-2 gap-6">
                            <div class="space-y-3">
                                <h3 class="text-xl font-semibold text-white">Innovation</h3>
                                <p class="text-black-300">Constantly pushing boundaries in technology and design</p>
                            </div>
                            <div class="space-y-3">
                                <h3 class="text-xl font-semibold text-white">Quality</h3>
                                <p class="text-black-300">Delivering excellence in every aspect of our work</p>
                            </div>
                            <div class="space-y-3">
                                <h3 class="text-xl font-semibold text-white">User Experience</h3>
                                <p class="text-black-300">Putting users first in everything we build</p>
                            </div>
                            <div class="space-y-3">
                                <h3 class="text-xl font-semibold text-white">Simplicity</h3>
                                <p class="text-black-300">Making complex things simple and accessible</p>
                            </div>
                        </div>
                    </div>

                    <div class="text-center">
                        <button class="btn-primary px-8 py-3 text-lg">
                            Get in Touch
                        </button>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>



