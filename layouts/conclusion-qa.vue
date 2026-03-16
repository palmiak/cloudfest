<script setup lang="ts">
import SlideChrome from '../components/SlideChrome.vue'

interface Props {
  accentColor?: 'green' | 'amber' | 'red'
  label?: string
}

const props = withDefaults(defineProps<Props>(), {
  accentColor: 'green'
})
</script>

<template>
  <div class="conclusion-qa-layout">
    <SlideChrome :accentColor="accentColor" />

    <div class="two-col">
      <div class="col-left">
        <div v-if="label" class="slide-label" :class="`label-${accentColor}`">
          {{ label }}
        </div>
        <slot name="conclusion" />
      </div>

      <div class="col-right">
        <slot name="qa" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.conclusion-qa-layout {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  padding: 0 var(--slide-padding-x);
  position: relative;
}

.two-col {
  display: flex;
  align-items: center;
  width: 100%;
  position: relative;
  z-index: 1;
}

.col-left {
  flex: 0 0 48%;
  padding-right: 8%;
  border-right: 1px solid var(--color-border-subtle);
  display: flex;
  flex-direction: column;
  gap: clamp(20px, 3vw, 36px);
}

.col-right {
  flex: 1;
  padding-left: 8%;
  display: flex;
  align-items: center;
}

.slide-label {
  font-size: var(--font-size-label);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 400;
}

.col-left :deep(h1),
.col-left :deep(h2) {
  font-family: var(--font-serif);
  font-size: var(--font-size-heading-xl);
  font-weight: 600;
  line-height: 1.1;
  color: var(--color-text-primary);
}

.col-right :deep(.qa-text) {
  font-family: var(--font-serif);
  font-size: clamp(18px, 3vw, 36px);
  font-weight: 400;
  font-style: italic;
  color: var(--color-text-faint);
  line-height: 1.3;
}

.col-left :deep(.contact-info) {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.col-left :deep(.contact-name) {
  font-size: clamp(11px, 1.3vw, 15px);
  font-weight: 400;
  color: var(--color-text-primary);
}

.col-left :deep(.contact-handle) {
  font-size: clamp(9px, 1.05vw, 12px);
  color: rgba(255, 255, 255, 0.35);
  font-weight: 300;
}
</style>
