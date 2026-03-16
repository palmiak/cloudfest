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
  <div class="two-column-layout">
    <SlideChrome :accentColor="accentColor" />

    <div class="two-col">
      <div class="col-left">
        <div v-if="label" class="slide-label" :class="`label-${accentColor}`">
          {{ label }}
        </div>
        <slot name="left" />
      </div>

      <div class="col-right">
        <slot name="right" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.two-column-layout {
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
  flex: 0 0 var(--col-left-width);
  padding-right: 6%;
  border-right: 1px solid var(--color-border-subtle);
}

.col-right {
  flex: 1;
  padding-left: 6%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: var(--gap-points);
}

.slide-label {
  font-size: var(--font-size-label);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 400;
  margin-bottom: clamp(8px, 1.2vw, 14px);
}

/* Make sure headings in left column have proper styling */
.col-left :deep(h1),
.col-left :deep(h2),
.col-left :deep(h3) {
  font-family: var(--font-serif);
  font-size: var(--font-size-heading);
  font-weight: 600;
  line-height: 1.15;
  color: var(--color-text-primary);
}
</style>
