<template>
    <div class="flex flex-col h-full">
      <div class="max-w-auto h-full border bg-gray-800 border-gray-700 rounded-lg flex flex-col">
        <div class="grid grid-cols-3 items-center m-2">
  <div class="justify-self-start">
    <CalendarViewSelector/>
  </div>
  <p class="text-white font-bold text-center text-4xl">
    {{ currentMonthString }}
  </p>
  <div class="justify-self-end">
    <AddEventButton/>
  </div>
</div>
      <hr class="pb-7 h-px bg-gray-900 border-0"/>
      <MonthView />
      </div>
    </div>
</template>

<script lang="ts">
import CalendarViewSelector from '@/Components/CalendarViewSelector.vue';
import MonthView from '@/Components/MonthView.vue';
import AddEventButton from './AddEventButton.vue';

export default {
  name: 'Month',
  components: {
    CalendarViewSelector,
    MonthView,
    AddEventButton
  },
  emits: ['getMonthString'],
  mounted() {
    this.$emit('getMonthString', this.currentMonthString);
  },
  data() {
    return {
      currentMonthString: new Date().toLocaleString('default', { month: 'long' }),
    };
  },
}

</script>