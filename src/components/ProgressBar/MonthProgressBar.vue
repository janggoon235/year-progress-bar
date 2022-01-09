<template>
  <label>month progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-red w3-round-xlarge" 
      :style="`width:${percent}`"
    >{{ percent }}</div>
  </div>
</template>

<script lang='ts'>
import { ref } from 'vue';
export default {
  setup(){
    let percent = ref('25%');
    const timeNow = new Date();
    const currentMonthStartPoint = new Date(timeNow.getFullYear(), timeNow.getMonth(), 1).getTime();
    const nextMonth = new Date(timeNow.getFullYear(), timeNow.getMonth() + 1, 1).getTime();
    const lengthOfOneMonth = nextMonth - currentMonthStartPoint;
    const monthGage = (timeNow.getTime() - currentMonthStartPoint)/lengthOfOneMonth;
    percent.value = `${(monthGage*100).toFixed(2)}%`;

    return {
      percent
    }
  }
}
</script>