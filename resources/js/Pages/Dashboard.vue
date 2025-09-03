<template>
  <PageLayout>
    <div class="w-full flex flex-col m-4 p-8 bg-gray-900 rounded-xl">
      <div class="flex">
        <TabMenu v-model:activeTab="selectedTab" :tabs="tabs" />
      </div>
      <CalendarView />
    </div>
  </PageLayout>
</template>

<script lang="ts">
import TabMenu from '@/Components/TabMenu.vue';
import CalendarView from '@/Components/CalendarView.vue';
import PageLayout from '@/Components/PageLayout.vue';
import { Tab } from '@/Interfaces/TabMenu';

export default {
  name: 'Dashboard',
  components: {
    TabMenu,
    CalendarView,
    PageLayout,
  },
  data() {
    return {
      selectedTab: 'present',
      tabs: [
        { key: 'present', label: 'Present' },
        { key: 'future', label: 'Future' },
        { key: 'past', label: 'Past' }
      ] as Tab[],
    };
  },
  methods: {
  }
}
</script>