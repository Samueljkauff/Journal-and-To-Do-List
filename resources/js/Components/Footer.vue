<template>
    <footer class="fixed bottom-0 left-0 w-full">
        <div :class="{'h-24': clicked}" class="flex justify-center items-center w-full bg-slate-800 h-12 text-white">
            <div  @click="onClick" class="flex items-center justify-center w-8 h-8 rounded-full hover:bg-slate-700 transition-colors duration-300 cursor-pointer">
            <i v-if="!clicked" class="fas fa-plus"></i>
            <i v-else class="fas fa-minus"></i>
            <p v-else >Github</p>
            </div>
        </div>
    </footer>
</template>

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
                // You can add more functionality here if needed
            }
        }
    };
</script>
