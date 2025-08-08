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

<script setup lang="ts">
import { useForm } from '@inertiajs/vue3';

const props = defineProps<{
    email: string;
    token: string;
}>();

const form = useForm({
    token: props.token,
    email: props.email,
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('password.store'), {
        onFinish: () => {
            form.reset('password', 'password_confirmation');
        },
    });
};
</script>
