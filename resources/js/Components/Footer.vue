<template>
    <footer class="fixed bottom-0 left-0 w-full">
        <div
            :class="{'h-24': clicked, 'h-12': !clicked}"
            class="flex justify-end pt-1 pr-[1rem] w-full bg-slate-800 text-white transition-all duration-300"
        >
            <transition name="icon-container-slide">
                <div
                    key="icon-container"
                    @click="onClick"
                    class="flex items-center justify-center w-8 h-8 rounded-full hover:bg-slate-700 transition-colors duration-300 cursor-pointer"
                >
                    <span>
                        <i v-if="!clicked" class="fas fa-plus"></i>
                        <i v-if="clicked" class="fas fa-minus"></i>
                    </span>
                </div>
            </transition>
        </div>
    </footer>
</template>

<style scoped>
.footer-slide-enter-active,
.footer-slide-leave-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.footer-slide-enter-from,
.footer-slide-leave-to {
  opacity: 0;
  transform: translateY(2rem);
}
.footer-slide-enter-to,
.footer-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>

<script lang="ts">
export default {
    name: 'Footer',
    data() {
        return {
            clicked: false,
        };
    },
    methods: {
        onClick() {
            this.clicked = !this.clicked;
        }
    }
};
</script>