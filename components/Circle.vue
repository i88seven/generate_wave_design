<template>
  <div class="circle">
  </div>
</template>

<script setup lang="ts">
interface Props {
  top: number
  left: number
  size: number
}

const props = withDefaults(defineProps<Props>(), {})
</script>

<style scoped>
.circle {
  display: inline-block;
  position: absolute;
  width: v-bind(size + 'px');
  height: v-bind(size + 'px');
  top: v-bind(top + 'px');
  left: v-bind(left + 'px');
  border-radius: 50%;
  border: 3px solid #0A8846;
  background: #007D3C;
}
</style>