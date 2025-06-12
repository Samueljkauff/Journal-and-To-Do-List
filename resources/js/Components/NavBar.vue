<template>
    <div class="text-white min-h-screen flex items-center justify-center">
        <nav :class="{ 'w-40': onNavClick, 'w-16': !onNavClick }"
            class="flex flex-col bg-slate-900 h-screen w-16 transition-all duration-300">
            <div
                @click="onLogoClick"
                class="flex justify-center py-4 hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:cursor-pointer"
            >
                <i class="fas fa-bars text-2xl"></i>
            </div>
            <div
                class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-purple-800 hover:to-indigo-800 hover:bg-slate-700"
                v-if="onNavClick"
            >
                <i class="fas fa-home inline" />
                <p class="inline">Home</p>
            </div>
            <div
                class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-purple-800 hover:to-indigo-800 hover:bg-slate-700"
                v-if="onNavClick"
            >
                <i class="fas fa-info-circle inline" />
                <p class="inline">About</p>
            </div>
            <div
                class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-purple-800 hover:to-indigo-800 hover:bg-slate-700"
                v-if="onNavClick"
            >
                <i class="fas fa-user inline" />
                <p class="inline">Profile</p>
            </div>
            <div
                class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-purple-800 hover:to-indigo-800 hover:bg-slate-700"
                v-if="onNavClick"
            >
                <i class="fas fa-cog inline" />
                <p class="inline">Settings</p>
            </div>
        </nav>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import '@fortawesome/fontawesome-free/css/all.css';

export default defineComponent({
    name: 'NavBar',
    data() {
        return {
            onNavClick: false,
        };
    },
    methods: {
        onLogoClick() {
            this.onNavClick = !this.onNavClick;
            console.log('Logo clicked:', this.onNavClick);
        }
    }
});
</script>