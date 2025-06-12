<template>
    <Head title="Welcome!" />

    <div class="min-h-screen flex items-center justify-center bg-slate-800">
        <div class="flex justify-start items-start w-full h-full">
            <NavBar />
        </div>
    </div>
</template>

<script setup lang="ts">
import NavBar from '@/Components/NavBar.vue';
</script>