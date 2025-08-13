<script setup lang="ts">
import Navbar from '~/components/Navbar.vue';


</script>

<template>
  <div class="min-h-screen bg-black-950">
    <Navbar />
    <main>
      <slot />
    </main>
  </div>
</template>
