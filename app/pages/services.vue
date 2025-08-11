<script setup lang="ts">
definePageMeta({
    layout: 'default'
})

const services = [
    {
        title: 'Web Development',
        description: 'Modern web applications built with cutting-edge technologies',
        icon: '💻'
    },
    {
        title: 'UI/UX Design',
        description: 'Beautiful and intuitive user interfaces that users love',
        icon: '🎨'
    },
    {
        title: 'Mobile Apps',
        description: 'Cross-platform mobile applications for iOS and Android',
        icon: '📱'
    },
    {
        title: 'Cloud Solutions',
        description: 'Scalable cloud infrastructure and deployment solutions',
        icon: '☁️'
    },
    {
        title: 'Consulting',
        description: 'Expert advice on technology strategy and implementation',
        icon: '💡'
    },
    {
        title: 'Training',
        description: 'Comprehensive training programs for your team',
        icon: '📚'
    }
]
</script>

<template>
    <main class="min-h-screen">
        <!-- Hero Section -->
        <section class="relative bg-gradient-primary text-white py-20">
            <div class="container mx-auto px-4 text-center">
                <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">
                    Our <span class="text-white">Services</span>
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-slide-up text-black-300">
                    Comprehensive solutions to help your business grow
                </p>
            </div>
        </section>

        <!-- Services Grid -->
        <section class="py-20 bg-black-900">
            <div class="container mx-auto px-4">
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div v-for="service in services" :key="service.title"
                        class="card text-center hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
                        <div class="text-6xl mb-4">{{ service.icon }}</div>
                        <h3 class="text-2xl font-semibold text-white mb-3">{{ service.title }}</h3>
                        <p class="text-black-300">{{ service.description }}</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- CTA Section -->
        <section class="py-20 bg-black-950 text-white">
            <div class="container mx-auto px-4 text-center">
                <h2 class="text-4xl font-bold mb-6">Ready to Get Started?</h2>
                <p class="text-xl text-black-300 mb-8 max-w-2xl mx-auto">
                    Let's discuss how we can help bring your vision to life
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <button class="btn-primary px-8 py-3 text-lg">
                        Start Project
                    </button>
                    <button class="btn-outline px-8 py-3 text-lg">
                        Schedule Call
                    </button>
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped>
.container {
    max-width: 1200px;
}
</style>
