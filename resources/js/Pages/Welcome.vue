<template>
    <div class="min-h-screen bg-black p-6">
        <div class="h-full min-h-[calc(100vh-3rem)] bg-gray-900 rounded-xl shadow-lg flex flex-col items-center justify-center relative">
                <Link href="/dashboard">
                    <i class="fas fa-calendar-days text-6xl text-green-500 mb-4"></i>
                </Link>
                <h1 class="text-3xl text-white mb-4">Welcome to the TooDoo</h1>
                <p class="text-gray-300 size">This is a simple application to keep track of your life!</p>
                <p class="text-gray-500 text-sm mt-2">Click the <i class="fas fa-calendar-days"></i> to start keeping track of your past Present and Future.</p>
            </div>
    </div>

</template>

<script setup lang="ts">
import { Link } from '@inertiajs/vue3';
</script>