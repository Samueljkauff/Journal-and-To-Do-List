<script setup lang="ts">
import { Link } from '@inertiajs/vue3';
</script>

<template>
  <div class="min-h-screen bg-black p-6">
    <div class="w-full h-full min-h-[calc(100vh-3rem)] bg-gray-900 rounded-xl shadow-lg flex flex-col items-center justify-center relative">
      <div class="absolute top-6 left-6">
        <Link href="/">
          <!-- Your logo/link content here -->
        </Link>
      </div>
      <div class="p-2 h-full border bg-gray-800 border-gray-700 rounded-lg">
              
        <slot />

      </div>
    </div>
  </div>
</template>