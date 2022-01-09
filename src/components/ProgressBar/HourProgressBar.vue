<template>
  <label>hour progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-pink w3-round-xlarge" 
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
    const currentTimeStartPoint = 
      new Date(
        timeNow.getFullYear(), 
        timeNow.getMonth(), 
        timeNow.getDate(), 
        timeNow.getHours()
      ).getTime();
    const hourGage = (timeNow.getTime() - currentTimeStartPoint)/(1000*60*60);
    percent.value = `${(hourGage*100).toFixed(2)}%`;
    return {
      percent
    }
  }
}
</script>