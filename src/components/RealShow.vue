<template>
<div>3333</div>
<img :src="data&&data.message" alt="png">
</template>
<script lang="ts">
import axios from 'axios'
import { defineComponent } from 'vue'
export default defineComponent({
    async setup() {
      const data = await axios.get('https://dog.ceo/api/breeds/image/random')
      console.log(data);
      return {
        data:data.data
      }
    }
})
</script>