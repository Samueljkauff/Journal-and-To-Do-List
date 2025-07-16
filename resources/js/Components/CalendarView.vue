<template>
  <div class="flex flex-col h-full">
    <div class="max-w-auto h-full border-2 border-gray-400 rounded-lg flex flex-col">
      <CalendarViewSelector />
        <hr class="pb-7"/>
            <div class="grid grid-cols-7 h-full w-full">
              <div v-for="day in getDaysOfMonth()" :key="day" class="p-2 border border-white text-white">
                {{ day }}
              </div>
            <div>
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
  methods:{
    getDaysOfMonth(): number[] {
      const days: number[] = [];
      const lastDay = new Date(this.currentYear, this.currentMonth + 1, 0).getDate();

      for (let i = 1; i <= lastDay; i++) {
        days.push(i);
      }

      return days;
    },
  }
};
</script>