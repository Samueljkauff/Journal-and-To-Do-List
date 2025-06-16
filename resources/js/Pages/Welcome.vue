<template>
    <Head title="Welcome!" />

    <div class="min-h-screen flex items-center justify-center bg-slate-800">
        <div class="flex justify-start items-start w-full h-full">
            <NavBar />
            <div class="w-full h-screen m-4 bg-slate-900 rounded-xl shadow-lg p-6">
                <div class="flex flex-col items-center justify-center h-full">
                    <i class="fas fa-calendar-days text-6xl text-green-500 mb-4"></i>
                    <h1 class="text-3xl text-white mb-4">Welcome to the TooDoo</h1>
                    <p class="text-gray-300 size">This is a simple application to keep track of your life!</p>
                    <p class="text-gray-500 text-sm mt-2">Click the Three bars to start keeping track of your past Present and Future.</p>
                </div>
                <Footer/>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
import Footer from '@/Components/Footer.vue';   
</script>