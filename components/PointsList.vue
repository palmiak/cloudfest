<script setup lang="ts">
interface Point {
  text: string
  color?: 'green' | 'amber' | 'red' | 'dim'
}

interface Props {
  points: Point[]
  defaultColor?: 'green' | 'amber' | 'red' | 'dim'
  allVisible?: boolean
}

withDefaults(defineProps<Props>(), {
  defaultColor: 'green',
  allVisible: false
})

const getDotClass = (color: string) => {
  return `point-dot-${color}`
}
</script>

<template>
  <div class="points">
    <template v-for="(point, index) in points" :key="index">
      <div v-if="allVisible || index === 0" class="point">
        <div
          class="point-dot"
          :class="getDotClass(point.color || defaultColor)"
        ></div>
        <div class="point-text" v-html="point.text"></div>
      </div>
      <div v-else class="point" v-click>
        <div
          class="point-dot"
          :class="getDotClass(point.color || defaultColor)"
        ></div>
        <div class="point-text" v-html="point.text"></div>
      </div>
    </template>
  </div>
</template>

<style scoped>
.points {
  display: flex;
  flex-direction: column;
  gap: var(--gap-points);
}

.point {
  display: flex;
  gap: var(--gap-point-dot);
  align-items: flex-start;
}

.point-dot {
  width: var(--point-dot-size);
  height: var(--point-dot-size);
  border-radius: 50%;
  flex-shrink: 0;
  margin-top: 0.5em;
  opacity: var(--opacity-point-dot);
}

.point-dot-green {
  background: var(--color-green);
}

.point-dot-amber {
  background: var(--color-amber);
}

.point-dot-red {
  background: var(--color-red);
}

.point-dot-dim {
  background: rgba(255, 255, 255, 0.3);
}

.point-text {
  font-size: var(--font-size-point);
  color: var(--color-text-primary);
  font-weight: 300;
  line-height: 1.4;
}
</style>
