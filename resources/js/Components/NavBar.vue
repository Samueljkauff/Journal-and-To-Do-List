<template>
    <div class="text-white min-h-screen flex flex-1 justify-start z-10">
        <nav :class="{ 'w-40': navClick, 'w-16': !navClick }"
            class="flex flex-col bg-gray-900 h-screen w-16 transition-all duration-300">
            <div
                @click="onNavClick"
                class="flex justify-center py-4 hover:bg-gradient-to-r hover:from-gray-700 hover:to-gray-900 hover:cursor-pointer"
            >
                <i class="fas fa-bars text-2xl"></i>
            </div>
            <transition-group
                name="fall"
                tag="div"
                class="flex flex-col"
            >
                <Link
                    v-if="navClick"
                    key="home"
                    href="/dashboard"
                    class="w-full flex justify-center items-center space-x-2 border-t border-gray-700 py-4 hover:cursor-pointer hover:bg-gradient-to-r hover:from-gray-700 hover:to-gray-900"
                >
                    <i class="fas fa-home inline" />
                    <p class="inline select-none">Home</p>
                </Link>
                <Link
                    v-if="navClick"
                    key="about"
                    href="/about"
                    class="w-full flex justify-center items-center space-x-2 border-t border-gray-700 py-4 hover:cursor-pointer hover:bg-gradient-to-r hover:from-gray-700 hover:to-gray-900"
                >
                    <i class="fas fa-info-circle inline" />
                    <p class="inline select-none">About</p>
                </Link>
                <Link
                    v-if="navClick"
                    key="profile"
                    href="/profile"
                    class="w-full flex justify-center items-center space-x-2 border-t border-gray-700 py-4 hover:cursor-pointer hover:bg-gradient-to-r hover:from-gray-700 hover:to-gray-900"
                >
                    <i class="fas fa-user inline" />
                    <p class="inline select-none">Profile</p>
                </Link>
                <Link
                    v-if="navClick"
                    key="settings"
                    href="/settings"
                    class="w-full flex justify-center items-center space-x-2 border-t border-gray-700 py-4 hover:cursor-pointer hover:bg-gradient-to-r hover:from-gray-700 hover:to-gray-900"
                >
                    <i class="fas fa-cog inline" />
                    <p class="inline select-none">Settings</p>
                </Link>
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
import { Link, Head } from '@inertiajs/vue3';

export default defineComponent({
    name: 'NavBar',
    components: {
        Link,
        Head
    },
    data() {
        return {
            navClick: false,
        };
    },
    methods: {
        onNavClick() {
            this.navClick = !this.navClick;
        }
    }
});
</script>