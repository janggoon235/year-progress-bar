<template>
  <label>day progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-yellow w3-round-xlarge" 
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
    const currentDayStartPoint = new Date(timeNow.getFullYear(), timeNow.getMonth(), timeNow.getDate()).getTime();
    const tommorrow = new Date(timeNow.getFullYear(), timeNow.getMonth(), timeNow.getDate() + 1).getTime();
    const lengthOfDay = tommorrow - currentDayStartPoint;
    const dayGage = (timeNow.getTime() - currentDayStartPoint)/lengthOfDay;
    percent.value = `${(dayGage*100).toFixed(2)}%`;
    return {
      percent
    }
  }
}
</script>
