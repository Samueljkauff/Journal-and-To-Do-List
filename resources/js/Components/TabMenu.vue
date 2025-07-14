<template>
    <Head title="Welcome!" />
    <div class="text-white text-xl w-full bg-slate-900 rounded-xl p-6 flex flex-row items-center justify-center">
        <span
            v-for="(label, key) in Tabs"
            :key="key"
            @click="setActiveTab(key)"
            class="flex justify-center items-center select-none cursor-pointer p-5 min-w-[109px] max-h-[28px] hover:bg-gradient-to-r hover:from-slate-900 hover:to-slate-700 hover:cursor-pointer"
            :class="{
                'border-b border-white font-bold': activeTab === key,
                'border-b border-gray-600': activeTab !== key
            }"
        >
            {{ label }}
        </span>
    </div>
</template>

<script lang="ts">
import { Link, Head } from '@inertiajs/vue3';

const Tabs = {
    past: 'Past',
    present: 'Present',
    future: 'Future',
} as const;

export default {
    components: { Link, Head },
    data() {
        return {
            activeTab: 'present',
            Tabs,
        };
    },
    methods: {
        setActiveTab(tab: string) {
            this.activeTab = tab;
        }
    },
};
</script>