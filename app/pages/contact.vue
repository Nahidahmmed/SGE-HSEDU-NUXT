<script setup lang="ts">
definePageMeta({
    layout: 'default'
})

const contactForm = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
});

const isSubmitting = ref(false);
const submitSuccess = ref(false);

const handleSubmit = async () => {
    if (!contactForm.value.name || !contactForm.value.email || !contactForm.value.message) {
        return;
    }

    isSubmitting.value = true;

    try {
        // Simulate API call
        await new Promise(resolve => setTimeout(resolve, 1000));

        // Success
        submitSuccess.value = true;
        contactForm.value = { name: '', email: '', subject: '', message: '' };

        // Reset success message after 5 seconds
        setTimeout(() => {
            submitSuccess.value = false;
        }, 5000);

    } catch (error) {
        console.error('Contact form error:', error);
    } finally {
        isSubmitting.value = false;
    }
};
</script>

<template>
    <main class="min-h-screen">
        <!-- Hero Section -->
        <section class="relative bg-gradient-primary text-white py-20">
            <div class="container mx-auto px-4 text-center">
                <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">
                    Contact <span class="text-white">Us</span>
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-slide-up text-black-300">
                    Get in touch with our team
                </p>
            </div>
        </section>

        <!-- Contact Form Section -->
        <section class="py-20 bg-black-900">
            <div class="container mx-auto px-4">
                <div class="max-w-2xl mx-auto">
                    <div class="card">
                        <h2 class="text-3xl font-bold text-white mb-8 text-center">Send us a Message</h2>

                        <!-- Success Message -->
                        <div v-if="submitSuccess"
                            class="mb-6 p-4 bg-green-900 border border-green-700 rounded-lg text-green-100">
                            Thank you! Your message has been sent successfully.
                        </div>

                        <form @submit.prevent="handleSubmit" class="space-y-6">
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Name</label>
                                    <input v-model="contactForm.name" type="text" class="input" placeholder="Your name"
                                        required />
                                </div>

                                <div class="form-group">
                                    <label class="form-label">Email</label>
                                    <input v-model="contactForm.email" type="email" class="input"
                                        placeholder="your@email.com" required />
                                </div>
                            </div>

                            <div class="form-group">
                                <label class="form-label">Subject</label>
                                <input v-model="contactForm.subject" type="text" class="input"
                                    placeholder="What's this about?" />
                            </div>

                            <div class="form-group">
                                <label class="form-label">Message</label>
                                <textarea v-model="contactForm.message" class="input min-h-[120px] resize-none"
                                    placeholder="Your message here..." required></textarea>
                            </div>

                            <button type="submit" :disabled="isSubmitting" class="w-full btn-primary py-3 text-lg">
                                <span v-if="isSubmitting" class="flex items-center justify-center">
                                    <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-black-950"
                                        xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                                        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor"
                                            stroke-width="4"></circle>
                                        <path class="opacity-75" fill="currentColor"
                                            d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
                                        </path>
                                    </svg>
                                    Sending...
                                </span>
                                <span v-else>Send Message</span>
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Info Section -->
        <section class="py-20 bg-black-950 text-white">
            <div class="container mx-auto px-4">
                <div class="max-w-4xl mx-auto text-center">
                    <h2 class="text-4xl font-bold mb-12">Other Ways to Reach Us</h2>

                    <div class="grid md:grid-cols-3 gap-8">
                        <div class="space-y-4">
                            <div class="text-4xl">📧</div>
                            <h3 class="text-xl font-semibold">Email</h3>
                            <p class="text-black-300">hello@sge-hsedu.com</p>
                        </div>

                        <div class="space-y-4">
                            <div class="text-4xl">📱</div>
                            <h3 class="text-xl font-semibold">Phone</h3>
                            <p class="text-black-300">+1 (555) 123-4567</p>
                        </div>

                        <div class="space-y-4">
                            <div class="text-4xl">📍</div>
                            <h3 class="text-xl font-semibold">Office</h3>
                            <p class="text-black-300">123 Tech Street<br>Digital City, DC 12345</p>
                        </div>
                    </div>
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
