<template>
    <Head title="Dashboard" />

    <div class="min-h-screen flex flex-col bg-slate-800">
        <div class="flex justify-start h-full">
            <NavBar />
            <div class="min-h-full w-full m-4 p-8 bg-slate-900 rounded-xl shadow-lg flex flex-col items-center">
                <TabMenu />
                <div class="h-full w-full p-5 border-2 border-gray-700 rounded-lg">
                    <CalenderViewSelector/>
                    <div class=" grid grid-cols-7">
                        <div v-for="day in daysInMonth()" :key="day" class="w-full h-full text-white border border-gray-700">Day {{ day }}</div>
                    </div>
                </div>
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
import CalenderViewSelector from '@/Components/CalenderViewSelector.vue';

function daysInMonth(year = new Date().getFullYear(), month = new Date().getMonth() + 1) {
    const numDays = new Date(year, month, 0).getDate();
    return Array.from({ length: numDays }, (_, i) => i + 1);
}
</script>