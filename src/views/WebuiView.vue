<template>
  <FloatBtn></FloatBtn>
  <div v-if="store.showFrame" class="iframe-container">
    <iframe id="ui-iframe" :src="store.service" frameborder="0"></iframe>
  </div>
  <Blank v-else></Blank>
</template>
<script lang="ts" setup>
import Blank from '@/views/BlankView.vue'
import FloatBtn from '@/components/FloatButton.vue'
import { useServiceStore } from '@/stores/service'
import { useUtils } from './useUtil'
const store = useServiceStore()
const { getUsername } = useUtils()

window.addEventListener('message', (event) => {
  let data = event.data
  if (data === 'request_user_info') {
    console.log('Message from child:', event.data)
    // 向子页面发送消息
    let iframe = document.querySelector('#ui-iframe') as HTMLIFrameElement
    if (iframe && iframe.contentWindow) {
      iframe.contentWindow.postMessage({ id: getUsername() }, store.service)
    }
  }
})
</script>
<style scoped>
.iframe-container {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background-color: white;
}

iframe {
  width: 100%;
  height: 100%;
}
</style>
