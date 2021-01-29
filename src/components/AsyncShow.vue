<template lang="">
  <div style="font-size:20px">
    {{result}}
  </div>
</template>
<script lang="ts">
import {defineComponent} from 'vue'
export default defineComponent({
  setup() {
    return new Promise((resolve, reject)=>{
      setTimeout(()=>{
        return resolve({result:'test async show'})
      }, 2000)
    })
  }
})
</script>