<script lang="ts" setup>
// import { ref } from 'vue'

import DragItem from '~/components/DragItem.vue'
import DropContainer from '~/components/DropContainer.vue'

const dragItems = ref([
  '1',
  '2',
  '3'
])
</script>

<template>
  <div class="container">
    <DropContainer :items="dragItems" />
    <DragItem v-for="item in dragItems" :key="item" :item="item" />
  </div>
</template>

<style scoped lang="scss">
.container {
  max-width: 1366px;
  padding: 50px;
  margin: 0 auto;
}
</style>
