<template>
  <PageLayout>
    <div class="w-full flex flex-col m-4 p-8 bg-gray-900 rounded-xl">
      <div class="flex">
        <TabMenu />
      </div>
      <CalendarView />
    </div>
  </PageLayout>
</template>

<script lang="ts">
import TabMenu from '@/Components/TabMenu.vue';
import CalendarView from '@/Components/CalendarView.vue';
import PageLayout from '@/Components/PageLayout.vue';

export default {
  name: 'Dashboard',
  components: {
    TabMenu,
    CalendarView,
    PageLayout,
  },
  data() {
    return {
    };
  },
  methods: {
  }
}
</script>