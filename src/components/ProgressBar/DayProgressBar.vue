<template>
  <label>day progress bar</label>
  <div 
    class="w3-light-grey w3-round-xlarge" 
    style="width:50%"
  >
    <div 
      class="w3-container w3-blue w3-round-xlarge" 
      style="width:25%"
    >{{percent}}</div>
  </div>
</template>

<script lang='ts'>
import { ref } from 'vue';
export default {
  setup(){
    let percent = ref('25%');
    return {
      percent
    }
  }
}
</script>

<style>

</style>