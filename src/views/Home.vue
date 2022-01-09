<template>
  <div class="home">
    <year-progress-bar/>
    <month-progress-bar/>
    <day-progress-bar/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import YearProgressBar from '@/components/ProgressBar/YearProgressBar.vue';
import MonthProgressBar from '@/components/ProgressBar/MonthProgressBar.vue';
import DayProgressBar from '@/components/ProgressBar/DayProgressBar.vue';

export default defineComponent({
  name: 'Home',
  components: {
    YearProgressBar,
    MonthProgressBar,
    DayProgressBar
  },
});
</script>
