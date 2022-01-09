<template>
  <label>minute progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-black w3-round-xlarge" 
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
    const currentMinuteStartPoint = 
      new Date(
        timeNow.getFullYear(), 
        timeNow.getMonth(), 
        timeNow.getDate(), 
        timeNow.getHours(),
        timeNow.getMinutes()
      ).getTime();
    const minuteGage = (timeNow.getTime() - currentMinuteStartPoint)/(1000*60);
    percent.value = `${(minuteGage*100).toFixed(2)}%`;
    return {
      percent
    }
  }
}
</script>