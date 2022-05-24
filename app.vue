<template>
  <div class="container">
    <div v-for="(position, index) in positions" :key="index">
      <CircleGroup :top="position.top" :left="position.left" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { circleSize, outerPadding } from '~/constants/index'

interface Position {
  top: number
  left: number
}
const heightPadding = circleSize / 4;
// const entireWidth = 375;
// const entireHeight = 667;
const entireWidth = (circleSize + outerPadding) * 2.5;
const entireHeight = entireWidth / 375 * 667;
const circleRows = 8;

const positions: Position[] = [];
for (let i = 0; i < circleRows; i++) {
  const leftAdjustment = i % 2 == 1 ? (circleSize + outerPadding) / 2 : 0;
  for (let j = 0; j < Math.floor(i / 2 + 1); j++) {
    positions.push({
      top: heightPadding * (circleRows - i - 2),
      left: entireWidth - leftAdjustment - (circleSize + outerPadding) * j,
    })
  }
}
for (let i = 0; i < circleRows; i++) {
  const leftAdjustment = i % 2 == 1 ? (circleSize + outerPadding) / 2 : 0;
  for (let j = 0; j < Math.floor(i / 2 + 1); j++) {
    positions.push({
      top: entireHeight - heightPadding * (circleRows - i - 2),
      left: leftAdjustment + (circleSize + outerPadding) * j,
    })
  }
}

</script>

<style scoped>
.container {
  display: inline-block;
  width: v-bind(entireWidth + 'px');
  height: v-bind(entireHeight + 'px');
  background: #007D3C;
}
</style>