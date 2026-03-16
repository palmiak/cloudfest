<script setup lang="ts">
interface Props {
  accentColor: 'green' | 'amber' | 'red'
}

defineProps<Props>()
</script>

<template>
  <div class="chrome-wrapper">
    <!-- Accent bar on left edge -->
    <div class="accent-bar" :class="`accent-${accentColor}`"></div>

    <!-- Top horizontal rule -->
    <div class="rule-top"></div>

    <!-- Bottom horizontal rule -->
    <div class="rule-bottom"></div>

    <!-- Corner dots -->
    <div class="dot dot-tr" :class="`dot-${accentColor}`"></div>
    <div class="dot dot-bl" :class="`dot-${accentColor}`"></div>
  </div>
</template>

<style scoped>
.chrome-wrapper {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.accent-bar {
  position: absolute;
  left: 0;
  top: 18%;
  bottom: 18%;
  width: 3px;
  border-radius: 0 2px 2px 0;
}

.accent-green {
  background: var(--color-green);
}

.accent-amber {
  background: var(--color-amber);
}

.accent-red {
  background: var(--color-red);
}

.rule-top {
  position: absolute;
  top: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: var(--color-border);
}

.rule-bottom {
  position: absolute;
  bottom: 11%;
  left: 9%;
  right: 9%;
  height: 1px;
  background: var(--color-border);
}

.dot {
  position: absolute;
  width: var(--dot-size);
  height: var(--dot-size);
  border-radius: 50%;
  opacity: var(--opacity-dot);
}

.dot-tr {
  top: 11%;
  right: 9%;
  transform: translate(50%, -50%);
}

.dot-bl {
  bottom: 11%;
  left: 9%;
  transform: translate(-50%, 50%);
}

.dot-green {
  background: var(--color-green);
}

.dot-amber {
  background: var(--color-amber);
}

.dot-red {
  background: var(--color-red);
}
</style>
