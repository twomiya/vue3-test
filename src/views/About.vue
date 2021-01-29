<template>
  <div class="about">
    {{nowTime}} {{getNowTime()}}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { nowTime, getNowTime } from "../hooks/useNowTime";



export default defineComponent({
  name: 'About',
  components: {
  },
  setup() {
    return{
      nowTime, 
      getNowTime
    }
  }
});
</script>
