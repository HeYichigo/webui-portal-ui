<template>
  <a-float-button
    shape="square"
    description="选择服务器"
    class="serve-select-btn"
    @click="showDrawer"
  >
    <template #icon>
      <DatabaseOutlined />
    </template>
  </a-float-button>
  <div v-if="store.showFrame" class="fixed-position fixed-content fixed-content-border">
    <p>{{ store.service_name }}</p>
    <p>当前使用人数: {{ store.service_count }}</p>
  </div>
  <a-drawer
    title="服务器列表"
    width="270"
    placement="right"
    :closable="false"
    :open="open"
    @close="onClose"
  >
    <Portal></Portal>
  </a-drawer>
</template>
<script lang="ts" setup>
import { DatabaseOutlined } from '@ant-design/icons-vue'
import Portal from '@/components/PortalComponent.vue'
import { useDrawer } from '@/components/useDrawer'
import { useServiceStore } from '@/stores/service'
const store = useServiceStore()
const { open, showDrawer, onClose } = useDrawer()
</script>
<style scoped>
.serve-select-btn {
  right: 50px;
  width: 60px;
  height: 55px;
  bottom: 50px;
}
.fixed-position {
  position: fixed;
  width: 150px;
  height: 55px;
  bottom: 50px;
  right: 120px;
}
.fixed-content {
  padding: 4px;
  background-color: rgb(255, 252, 252);
}
.fixed-content-border {
  outline: dashed grey;
  outline-width: 1px;
  border-radius: 8px;
}
</style>
