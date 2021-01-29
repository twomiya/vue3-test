<template lang="">
  <div>
    <img :src="result&&result.message"/>
  </div>
</template>
<script lang="ts">
import {ref} from 'vue'
import useUrlAxios from '../hooks/useURLAxios'
const app = {
  name: 'test',
  setup() {
    const { result, loading, loaded} = useUrlAxios('https://dog.ceo/api/breeds/image/random')

    return {
      result,
      loading,
      loaded
    }
  }
}
export default app
</script>