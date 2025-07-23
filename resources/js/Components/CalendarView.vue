<template>
  <div class="flex flex-col h-full">
    <div class="max-w-auto h-full border bg-gray-800 border-gray-700 rounded-lg flex flex-col">
      <CalendarViewSelector />
      <hr class="pb-7 h-px bg-gray-900 border-0"/>
      <div class="grid grid-cols-7 h-full w-full border-l border-t border-gray-900">
        <div
          v-for="(days) in getDaysOfMonth()"
          :key="days"
          class="p-2 text-white border-r border-b border-gray-900 hover:bg-gray-700">
          {{ days }}
        </div>
        <div 
          v-for="n in getEmptyCellsCount()" 
          :key="'empty-' + n"
          class="p-2 border-b border-gray-900">
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import CalendarViewSelector from '@/Components/CalendarViewSelector.vue';

export default {
  name: 'DefaultComponent',
  data() {
    return {
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
    };
  },
  components: {
    CalendarViewSelector,
  },
  methods: {
    getDaysOfMonth(): number[] {
      const days: number[] = [];
      const lastDay = new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
      for (let i = 1; i <= lastDay; i++) {
        days.push(i);
      }
      return days;
    },
    getEmptyCellsCount(): number {
      const totalDays = this.getDaysOfMonth().length;
      const totalCells = Math.ceil(totalDays / 7) * 7;
      return totalCells - totalDays;
    }
  }
};
</script>