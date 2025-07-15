<template>
    <div class="h-full w-full p-5 border-2 border-gray-400 rounded-lg">
      <CalendarViewSelector />
        <hr class="pb-7"/>
        <div class="grid grid-cols-2">
            <div class="grid grid-cols-7">
              <div v-for="day in getDaysOfMonth()" :key="day" class="aspect-square p-4 border border-white text-white rounded w-w-28 max-h-28">
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
  components: {
    CalendarViewSelector,
  },
  methods:{
    getDaysOfMonth(): number{
      const numDaysInMonth = 31;
      return numDaysInMonth;
    },
  }
};
</script>