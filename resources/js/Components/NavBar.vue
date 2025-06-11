<template>
    <div class="text-white min-h-screen flex items-center justify-center">
        <nav :class="{ 'w-40': logoClicked, 'w-16': !logoClicked }"
            class="flex flex-col bg-slate-900 h-screen w-16 transition-all duration-300">
            <button class="hover:cursor-pointer" @click="onLogoClick">(Clickable LOGO)</button>

            <div
                class="mx-auto flex items-center space-x-2 border-t border-slate-900 py-4"
                v-if="logoClicked"
            >
                <i class="fas fa-home inline" />
                <p class="inline">Home</p>
            </div>
            <hr class="border-t border-slate-700 my-2 mx-4" v-if="logoClicked" />
            <div
                class="mx-auto flex items-center space-x-2 py-4"
                v-if="logoClicked"
            >
                <i class="fas fa-info-circle inline" />
                <p class="inline">About</p>
            </div>
            <hr class="border-t border-slate-700 my-2 mx-4" v-if="logoClicked" />
            <div
                class="mx-auto flex items-center space-x-2 py-4"
                v-if="logoClicked"
            >
                <i class="fas fa-user inline" />
                <p class="inline">Profile</p>
            </div>
            <hr class="border-t border-slate-700 my-2 mx-4" v-if="logoClicked" />
            <div
                class="mx-auto flex items-center space-x-2 py-4"
                v-if="logoClicked"
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
            logoClicked: false,
        };
    },
    methods: {
        onLogoClick() {
            this.logoClicked = !this.logoClicked;
            console.log('Logo clicked:', this.logoClicked);
        }
    }
});
</script>