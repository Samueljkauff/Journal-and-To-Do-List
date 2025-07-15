<template>
    <Head title="Dashboard" />

    <div class="min-h-screen flex flex-col bg-slate-800">
        <div class="flex justify-start h-full">
            <NavBar />
            <div class="min-h-full w-full m-4 p-8 bg-slate-900 rounded-xl shadow-lg flex flex-col items-center">
                <TabMenu />
                    <WeekView />
            </div>
            <!-- <Footer/> -->
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
// import Footer from '@/Components/Footer.vue';
import { Head } from '@inertiajs/vue3'; 
import TabMenu from '@/Components/TabMenu.vue';
import WeekView from '@/Components/MonthView.vue';
</script>