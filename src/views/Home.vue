<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <Modal />
    <Suspense>
      <template #default>
        <AsyncShow />
      </template>
      <template #fallback>
        <h1>Loading...</h1>
      </template>
    </Suspense>
    
    <Suspense>
      <template #default>
        <RealShow/>
      </template>
      <template #fallback>
        <h1>Loading...</h1>
      </template>
    </Suspense>
  </div>
</template>

<script lang="ts">
import { defineComponent,onErrorCaptured } from 'vue';
import Modal from "@/components/Modal.vue";
import AsyncShow from "@/components/AsyncShow.vue";
import RealShow from "@/components/RealShow.vue";

import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    HelloWorld,
    Modal,
    AsyncShow,
    RealShow
  },
  setup() {
    onErrorCaptured((error) => {
        console.log(`error====>`,error)
        return true  
      })
  }
});
</script>
