<template>
  <div class="text-white px-2 my-auto space-x-4 max-w-fit rounded-lg">
    <span
      v-for="(view, idex) in views"
      :key="view.key"
      @click="setActiveView(view.key)"
      :class="[
        'cursor-pointer px-1 rounded-lg font-bold hover:bg-gray-700 p-1',
        idex <= activeViewIndex ? 'text-white' : 'text-gray-600'
      ]"
    >
      {{ view.label }}
      <i v-if="view.key !== 'today'" class="fas fa-arrow-right"></i>
    </span>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      views: [
        { key: 'year', label: 'Year' },
        { key: 'month', label: 'Month' },
        { key: 'today', label: 'Today' },
      ],
      activeView: 'today',
    };
  },
  computed: {
    activeViewIndex(): number {
      return this.views.findIndex(v => v.key === this.activeView);
    },
  },
  methods: {
    setActiveView(key: string) {
      this.activeView = key;
    },
  },
});
</script>