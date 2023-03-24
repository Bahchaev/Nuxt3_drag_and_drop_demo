<script lang="ts" setup>
import { ref } from 'vue'

import DragItem from '~/components/DragItem.vue'

function onDrop (e: DragEvent): void {
  const item = e.dataTransfer!.getData('itemId')
  items.value.push(item)
  console.log('drop', item)
}

const items = ref<string[]>([])
</script>

<template>
  <div
    class="drop-container"
    @drop="onDrop"
    @dragover.prevent
    @dragenter.prevent
  >
    <DragItem v-for="item in items" :key="item" :item="item" />
  </div>
</template>

<style scoped lang="scss">
.drop-container {
  width: 100%;
  height: 500px;
  border: 1px solid $grey;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}
</style>
