<template>
    <Head title="{WHATEVER}" />

    <div class="flex flex-col bg-black min-h-screen">
        <div class="flex justify-start h-full">
            <NavBar />
            <slot class="flex-1 flex flex-col">

            </slot>
            <!-- <Footer/> -->
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
import Footer from '@/Components/Footer.vue';
import { Head } from '@inertiajs/vue3'; 
</script>