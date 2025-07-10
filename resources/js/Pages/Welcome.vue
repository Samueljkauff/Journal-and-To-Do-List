<template>
    <Head title="Welcome!" />

    <div class="min-h-screen flex flex-col bg-slate-800">
        <div class="flex justify-start">
            <NavBar />
            <div class="w-full mt-4 ml-4 mr-4 bg-slate-900 rounded-xl shadow-lg p-6 flex flex-col items-center justify-center">
                <Link href="/dashboard">
                    <i class="fas fa-calendar-days text-6xl text-green-500 mb-4"></i>
                </Link>
                <h1 class="text-3xl text-white mb-4">Welcome to the TooDoo</h1>
                <p class="text-gray-300 size">This is a simple application to keep track of your life!</p>
                <p class="text-gray-500 text-sm mt-2">Click the Three bars to start keeping track of your past Present and Future.</p>
            </div>
            <Footer/>
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
import Footer from '@/Components/Footer.vue';
import { Link } from '@inertiajs/vue3'; 
</script>