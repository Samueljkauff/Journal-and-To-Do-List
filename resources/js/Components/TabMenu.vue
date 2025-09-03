<template>
    <div class="text-xl max-w-[327px] m-auto bg-gray-900 rounded-xl pb-6 flex flex-row items-center justify-center">
        <span
            v-for="tab in tabs"
            :key="tab.key"
            @click="() => setActiveTab(tab.key)"
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
import { PropType } from 'vue';
import { Tab } from '@/Interfaces/TabMenu';

export default {
    components: { Head },
    emits: ['update:activeTab'],
    props: {
        activeTab: {
            type: String,
            required: true
        },
        tabs: {
            type: Array as PropType<Tab[]>,
            required: true,
        }
    },
    methods: {
        setActiveTab(tab: string) {
            this.$emit('update:activeTab', tab);
        }
    },
};
</script>