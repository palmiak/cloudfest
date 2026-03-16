<script setup lang="ts">
import SlideChrome from '../components/SlideChrome.vue'

interface Props {
  accentColor?: 'green' | 'amber' | 'red'
}

const props = withDefaults(defineProps<Props>(), {
  accentColor: 'green'
})
</script>

<template>
  <div class="full-width-layout">
    <SlideChrome :accentColor="accentColor" />

    <div class="content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.full-width-layout {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 var(--slide-padding-x);
  position: relative;
}

.content {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  z-index: 1;
}

.content :deep(h1),
.content :deep(h2),
.content :deep(h3) {
  font-family: var(--font-serif);
  font-size: var(--font-size-heading);
  font-weight: 600;
  line-height: 1.15;
  color: var(--color-text-primary);
}

.content :deep(.slide-label) {
  font-size: var(--font-size-label);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 400;
  margin-bottom: clamp(10px, 2vw, 20px);
}
</style>
