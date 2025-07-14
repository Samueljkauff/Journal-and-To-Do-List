<template>
    <Head title="Dashboard" />

    <div class="min-h-screen flex flex-col bg-slate-800">
        <div class="flex justify-start">
            <NavBar />
            <div class="w-full m-4 bg-slate-900 rounded-xl shadow-lgflex flex-col items-center">
                <TabMenu />
            </div>
            <!-- <Footer/> -->
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
// import Footer from '@/Components/Footer.vue';
import { Link, Head } from '@inertiajs/vue3'; 
import TabMenu from '@/Components/TabMenu.vue';
</script>