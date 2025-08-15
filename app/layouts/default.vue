<script setup lang="ts">
import Footer from "~/components/Footer.vue";
import Navbar from "~/components/Navbar.vue";
</script>

<template>
  <div class="min-h-screen bg-black-950">
    <Navbar />
    <main>
      <slot />
    </main>
    <Footer />
  </div>
</template>
