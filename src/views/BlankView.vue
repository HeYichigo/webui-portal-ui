<script lang="ts" setup>
import { useServiceStore } from '@/stores/service'

const store = useServiceStore()
</script>

<template>
  <div v-if="store.loading" class="loading-spin">
    <a-spin tip="加载中..." />
  </div>
  <div v-else class="notice notice-font">
    <p>请点击右下角按钮</p>
    <p style="font-size: large">Select a server please.</p>
    <p>选择comfyui服务</p>
    <div class="copyright">© 吉林省瑞宸科技有限公司 版权所有</div>
  </div>
  <div class="frount-page-background">
    <video class="background-video" preload="auto" loop playsinline autoplay tabindex="-1" muted
      src="@/assets/frount.mp4"></video>
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

.text {
  font-size: 100pt;
}

/* 版权信息容器 */
.copyright {
  /* 核心：固定定位，贴在页面底部 */
  position: fixed;
  bottom: 0;
  /* 距离页面下边缘 0 像素 */
  left: 50%;
  /* 水平居中第一步：左边缘对齐页面50%位置 */
  transform: translateX(-50%);
  /* 水平居中第二步：向左偏移自身50%，实现完美居中 */

  /* 可选样式：提升视觉效果 */
  width: 100%;
  /* 宽度铺满（也可自定义宽度，如 80%） */
  padding: 10px 0;
  /* 上下内边距，避免文字贴边 */
  background-color: #f5f5f5;
  /* 浅灰色背景，区分内容 */
  text-align: center;
  /* 文字水平居中（兜底，防止 transform 失效） */
  font-size: 12px;
  /* 小号字体，不抢视觉焦点 */
  color: #666;
  /* 灰色文字，弱化视觉 */
  border-top: 1px solid #eee;
  /* 顶部细线，分隔页面内容 */
  z-index: 9999;
  /* 确保悬浮在所有元素上方（避免被其他内容遮挡） */
}
</style>
