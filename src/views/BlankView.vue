<script lang="ts" setup>
import { useServiceStore } from '@/stores/service'

const store = useServiceStore()
</script>

<template>
  <div v-if="store.loading" class="loading-spin">
    <a-spin tip="加载中..." />
  </div>
  <div v-else class="notice notice-font">
    <p>当前未选择服务器</p>
    <p style="font-size: large">Select a server please.</p>
    <p>请点击右下角按钮进行选择</p>
  </div>
  <div class="frount-page-background">
    <video
      class="background-video"
      preload="auto"
      loop
      playsinline
      autoplay
      tabindex="-1"
      muted
      src="@/assets/frount.mp4"
    ></video>
  </div>
</template>

<style scoped>
.loading-spin {
  text-align: center;
  background-color: rgba(255, 255, 255, 0);
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 40%;
}
</style>
