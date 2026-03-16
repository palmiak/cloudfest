<script setup lang="ts">
interface Props {
  value: string
  label: string
  color?: 'green' | 'amber' | 'red'
}

withDefaults(defineProps<Props>(), {
  color: 'green'
})
</script>

<template>
  <div class="stat-box">
    <div class="stat-value">{{ value }}</div>
    <div class="stat-label">{{ label }}</div>
  </div>
</template>

<style scoped>
/* Styles inherited from global index.css */
</style>
