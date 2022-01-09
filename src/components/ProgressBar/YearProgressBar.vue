<template>
  <label>year progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-blue w3-round-xlarge" 
      :style="`width:${percent}`"
    >{{ percent }}</div>
  </div>
</template>

<script lang='ts'>
import { ref } from 'vue';
export default {
  name: 'YearProgressBar',
  setup(){
    let percent = ref('25%');
    /** 현재시간 */
    const timeNow = new Date();
    const currentYearStartPoint = new Date(timeNow.getFullYear(), 0, 1).getTime();
    const nextYear = new Date(timeNow.getFullYear() + 1, 0, 1).getTime();
    const lengthOfOneYear = nextYear - currentYearStartPoint;
    const yearGage = (timeNow.getTime() - currentYearStartPoint)/lengthOfOneYear;
    percent.value = `${(yearGage*100).toFixed(2)}%`;

    return {
      percent
    }
  }
}
</script>