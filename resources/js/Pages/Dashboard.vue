<template>
  <PageLayout>
    <div class="w-full flex flex-col m-4 p-8 bg-gray-900 rounded-xl">
      <div class="flex">
        <!-- <div class="pb-6 text-white text-3xl font-semibold">
            {{ currentMonth }}
        </div> -->
        <TabMenu />
      </div>
      <CalendarView @get-month-string="getMonthString" />
    </div>
  </PageLayout>
</template>

<script lang="ts">
import TabMenu from '@/Components/TabMenu.vue';
import CalendarView from '@/Components/CalendarView.vue';
import PageLayout from '@/Components/PageLayout.vue';
import AddEventButton from '@/Components/AddEventButton.vue';

export default {
  name: 'Dashboard',
  components: {
    TabMenu,
    CalendarView,
    PageLayout,
    AddEventButton
  },
  data() {
    return {
      currentMonth: ''
    };
  },
  methods: {
    getMonthString(monthString: string) {
      this.currentMonth = monthString;
    }
  }
}
</script>