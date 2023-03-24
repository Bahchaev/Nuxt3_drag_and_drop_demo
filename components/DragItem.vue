<script lang="ts" setup>
import { ref } from 'vue'

interface IProps {
  item: any
}

const props = withDefaults(defineProps<IProps>(), {
})

const isDragging = ref(false)

function onDragStart (e: DragEvent, item: IProps['item']): void {
  isDragging.value = true
  e.dataTransfer!.dropEffect = 'move'
  e.dataTransfer!.effectAllowed = 'move'
  e.dataTransfer!.setData('itemID', item)
  console.log('drag start', item)
}
function onDragEnd (): void {
  isDragging.value = false
}
function onDrag (e: DragEvent):void {
  console.log('drag')
}
function onDragEnter (e: DragEvent): void {
  console.log('drag enter')
}
function onDragOver (e:DragEvent):void {
  console.log('drag over')
}
function onDragLeave (e: DragEvent): void {
  console.log('drag leave')
}
function onDrop (e: DragEvent): void {
  console.log('drop')
}
</script>

<template>
  <div
    class="drag-item"
    :class="{
      'is-dragging': isDragging
    }"
    draggable="true"
    @dragstart="(e) => onDragStart(e, item)"
    @drag="onDrag"
    @dragend="onDragEnd"
    @dragenter="onDragEnter"
    @dragover="onDragOver"
    @dragleave="onDragLeave"
    @drop="onDrop"
  >
    {{ item }}
  </div>
</template>

<style scoped lang="scss">
.drag-item {
  width: 50px;
  height: 50px;
  border: 3px solid $black;
  background: $blue;
  cursor: move;
}

.is-dragging {
  background: $red;
}
</style>
