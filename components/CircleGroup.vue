<template>
  <div>
    <template v-for="index in 5" :key="index">
      <Circle :top="generateTop(index)" :left="generateLeft(index)" :size="generateSize(index)" />
    </template>
  </div>
</template>

<script setup lang="ts">
import { circleSize, innerPadding } from '~/constants/index'

interface Props {
  // center の position
  top: number
  left: number
}

const props = withDefaults(defineProps<Props>(), {
  top: 0,
  left: 0
})

const generateTop = (index: number): number => {
  return props.top + innerPadding * index - circleSize / 2;
}
const generateLeft = (index: number): number => {
  return props.left + innerPadding * index - circleSize / 2;
}
const generateSize = (index: number): number => {
  return circleSize - innerPadding * 2 * index;
}
</script>

<style scoped>
</style>