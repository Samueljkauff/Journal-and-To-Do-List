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
            <transition-group
                name="fall"
                tag="div"
                class="flex flex-col"
            >
                <div
                    v-if="onNavClick"
                    key="home"
                    class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:bg-slate-700"
                >
                    <i class="fas fa-home inline" />
                    <p class="inline">Home</p>
                </div>
                <div
                    v-if="onNavClick"
                    key="about"
                    class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:bg-slate-700"
                >
                    <i class="fas fa-info-circle inline" />
                    <p class="inline">About</p>
                </div>
                <div
                    v-if="onNavClick"
                    key="profile"
                    class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:bg-slate-700"
                >
                    <i class="fas fa-user inline" />
                    <p class="inline">Profile</p>
                </div>
                <div
                    v-if="onNavClick"
                    key="settings"
                    class="w-full flex justify-center items-center space-x-2 border-t border-slate-700 py-4 hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:bg-slate-700"
                >
                    <i class="fas fa-cog inline" />
                    <p class="inline">Settings</p>
                </div>
            </transition-group>
        </nav>
    </div>
</template>

<style scoped>
.fall-enter-active {
  transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
}
.fall-leave-active {
  transition: all 1s cubic-bezier(0.23, 1, 0.32, 1);
}
.fall-enter-from {
  opacity: 0;
  transform: translateY(-40px) scaleY(0.7);
}
.fall-enter-to {
  opacity: 1;
  transform: translateY(0) scaleY(1);
}
.fall-leave-from {
  opacity: 1;
  transform: translateY(0) scaleY(1);
}
.fall-leave-to {
  opacity: 0;
  transform: translateX(-200px) scaleY(0.7);
}
</style>

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