<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'SuccessPage',
})
const pictrueUrl = ref<string>('/kfc-vwo50/kfc6.jpeg')
</script>

<template>
  <div flex flex-col items-center>
    <img :src="pictrueUrl" alt="" h-128 w-128>
    有你真好～
  </div>
</template>
