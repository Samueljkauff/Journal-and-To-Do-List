<template>
    <PageLayout>
        <div class="w-full flex flex-col m-4 p-8 bg-gray-900 rounded-xl">
            <TabMenu />
            <CalendarView />
        </div>
    </PageLayout>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
// import Footer from '@/Components/Footer.vue';
import { Head } from '@inertiajs/vue3'; 
import TabMenu from '@/Components/TabMenu.vue';
import CalendarView from '@/Components/CalendarView.vue';
import PageLayout from '@/Components/PageLayout.vue';
</script>