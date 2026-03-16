<script setup lang="ts">
import SlideChrome from '../components/SlideChrome.vue'

interface Props {
  accentColor?: 'green' | 'amber' | 'red'
  eyebrow?: string
}

const props = withDefaults(defineProps<Props>(), {
  accentColor: 'green'
})
</script>

<template>
  <div class="title-slide-layout">
    <SlideChrome :accentColor="accentColor" />

    <div class="content">
      <div v-if="eyebrow" class="eyebrow" :class="`label-${accentColor}`">
        {{ eyebrow }}
      </div>
      <slot />
    </div>
  </div>
</template>

<style scoped>
.title-slide-layout {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 var(--slide-padding-x);
  position: relative;
}

.content {
  width: 100%;
  text-align: center;
  position: relative;
  z-index: 1;
}

.eyebrow {
  font-size: var(--font-size-label);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 400;
  margin-bottom: clamp(16px, 2.5vw, 28px);
}

.content :deep(h1) {
  font-family: var(--font-serif);
  font-size: var(--font-size-heading-xl);
  font-weight: 600;
  line-height: 1.1;
  color: var(--color-text-primary);
}
</style>
