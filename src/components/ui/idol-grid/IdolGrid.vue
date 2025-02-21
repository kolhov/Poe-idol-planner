<script setup lang="ts">
import 'gridstack/dist/gridstack.min.css';
import 'gridstack/dist/gridstack-extra.min.css';
import {GridStack, type GridStackWidget} from 'gridstack';
import {onMounted, ref} from "vue";
import ImageItem from "@/components/ui/image-item/ImageItem.vue"
import type {extGridStackWidget} from "@/lib/types/extGridStack.ts";

const gridRef = ref(null);

const defaultItem = {locked: true, imageSrc: '/defaultItem.png', noMove: true};
const items = ref<extGridStackWidget[]>([
  { id: '111x', x: 0, y: 0, ...defaultItem },
  { id: '211x', x: 1, y: 2, ...defaultItem },
  { id: '311x', x: 1, y: 3, ...defaultItem },
  { id: '411x', x: 1, y: 4, ...defaultItem },
  { id: '511x', x: 2, y: 3, ...defaultItem },
  { id: '611x', x: 3, y: 3, ...defaultItem },
  { id: '711x', x: 4, y: 2, ...defaultItem },
  { id: '811x', x: 4, y: 3, ...defaultItem },
  { id: '911x', x: 4, y: 4, ...defaultItem },
  { id: '011x', x: 5, y: 6, ...defaultItem },
  { id: '011x', x: 5, y: 6, imageSrc: '/defaultItem.png', h: 2 },
]);

onMounted(() => {
  if (gridRef.value) {
    GridStack.init({
      float: true,
      cellHeight: "40px",
      row: 7,
      column: 6,
      disableResize: true,
      margin: 0,
    }, gridRef.value);
  }
});
</script>

<template>
  <div class="flex items-center justify-center h-screen">
  <div ref="gridRef" class="grid-stack bg-muted">
    <div
      v-for="widget in items"
      :key="widget.id"
      :gs-x="widget.x"
      :gs-y="widget.y"
      :gs-w="widget.w"
      :gs-h="widget.h"
      :gs-locked="widget.locked"
      :gs-no-move="widget.noMove"
      class="grid-stack-item"
    >
      <div class="grid-stack-item-content">
        <ImageItem :imageSrc="widget.imageSrc" />
      </div>
    </div>
  </div>
  </div>
</template>

<style scoped>
.grid-stack-item-content {
  background-color: #18BC9C;
}
.grid-stack {
  width: 240px;
  height: 280px;
}
.grid-stack {
  @apply flex justify-center items-center;
}
</style>
