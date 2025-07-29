<template>
    <div class="text-xl max-w-[327px] m-auto bg-gray-900 rounded-xl pb-6 flex flex-row items-center justify-center">
        <span
            v-for="tab in tabs"
            :key="tab.key"
            @click="setActiveTab(tab.key)"
            class="flex justify-center items-center select-none cursor-pointer p-5 min-w-[109px] max-h-[28px] text-white hover:font-bold hover:bg-gradient-to-t hover:from-gray-700 hover:to-gray-900"
            :class="{
                'border-b-2 border-white font-bold': activeTab === tab.key,
                'border-b border-gray-600': activeTab !== tab.key
            }"
        >
            {{ tab.label }}
        </span>
    </div>
</template>

<script lang="ts">
import { Head } from '@inertiajs/vue3';

export default {
    components: { Head },
    data() {
        return {
            activeTab: 'present',
            tabs: [
                { key: 'past', label: 'Past' },
                { key: 'present', label: 'Present' },
                { key: 'future', label: 'Future' },
            ],
        };
    },
    methods: {
        setActiveTab(tab: string) {
            this.activeTab = tab;
        }
    },
};
</script>