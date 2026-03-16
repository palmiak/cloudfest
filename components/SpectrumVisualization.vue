<script setup lang="ts">
interface AxisPoint {
  text: string
  color: string
}

interface Props {
  leftPlayer: string
  leftPlayerSub: string
  rightPlayer: string
  rightPlayerSub: string
  leftPoints: AxisPoint[]
  rightPoints: AxisPoint[]
  allVisible?: boolean
}

withDefaults(defineProps<Props>(), {
  allVisible: false
})
</script>

<template>
  <div class="spectrum-wrap">
    <div class="spectrum-players">
      <div>
        <div class="player-name" style="color: var(--color-blue);">{{ leftPlayer }}</div>
        <div class="player-sub">{{ leftPlayerSub }}</div>
      </div>
      <div style="text-align: right;">
        <div class="player-name" style="color: var(--color-green);">{{ rightPlayer }}</div>
        <div class="player-sub">{{ rightPlayerSub }}</div>
      </div>
    </div>

    <div class="spectrum-track">
      <div class="track-dot" style="left: 0%; background: var(--color-blue);"></div>
      <div class="track-dot" style="left: 100%; background: var(--color-green);"></div>
      <div class="neither-pill">neither is better</div>
    </div>

    <div class="spectrum-axis">
      <div class="axis-side">
        <template v-for="(point, index) in leftPoints" :key="`left-${index}`">
          <div v-if="allVisible" class="axis-label">
            <span class="axis-dot" :style="{ background: point.color }"></span>
            {{ point.text }}
          </div>
          <div v-else class="axis-label" v-click>
            <span class="axis-dot" :style="{ background: point.color }"></span>
            {{ point.text }}
          </div>
        </template>
      </div>
      <div class="axis-side right">
        <template v-for="(point, index) in rightPoints" :key="`right-${index}`">
          <div v-if="allVisible" class="axis-label">
            <span class="axis-dot" :style="{ background: point.color }"></span>
            {{ point.text }}
          </div>
          <div v-else class="axis-label" v-click>
            <span class="axis-dot" :style="{ background: point.color }"></span>
            {{ point.text }}
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<style scoped>
.spectrum-wrap {
  width: 100%;
}

.spectrum-players {
  display: flex;
  justify-content: space-between;
  margin-bottom: var(--spacing-2xl);
}

.player-name {
  font-size: var(--font-size-player);
  font-weight: 600;
}

.player-sub {
  font-size: var(--font-size-player-sub);
  color: rgba(255, 255, 255, 0.35);
  font-weight: 300;
}

.spectrum-track {
  width: 100%;
  height: 3px;
  background: linear-gradient(
    to right,
    var(--color-blue),
    rgba(255, 255, 255, 0.1) 45%,
    rgba(255, 255, 255, 0.1) 55%,
    var(--color-green)
  );
  border-radius: 2px;
  position: relative;
}

.track-dot {
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  width: var(--track-dot-size);
  height: var(--track-dot-size);
  border-radius: 50%;
  border: 2px solid var(--color-bg);
}

.neither-pill {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: var(--color-bg);
  border: 1px solid rgba(255, 255, 255, 0.22);
  border-radius: var(--radius-pill);
  padding: clamp(3px, 0.5vw, 5px) var(--spacing-lg);
  white-space: nowrap;
  font-size: var(--font-size-spectrum-pill);
  font-weight: 400;
  color: var(--color-text-secondary);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.spectrum-axis {
  display: flex;
  justify-content: space-between;
  margin-top: var(--gap-points);
  gap: 16px;
}

.axis-side {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xs);
  flex: 1;
}

.axis-side.right {
  align-items: flex-end;
}

.axis-label {
  font-size: var(--font-size-axis);
  color: rgba(255, 255, 255, 0.38);
  font-weight: 300;
  display: flex;
  align-items: center;
  gap: 6px;
}

.axis-side.right .axis-label {
  flex-direction: row-reverse;
}

.axis-dot {
  width: var(--dot-size);
  height: var(--dot-size);
  border-radius: 50%;
  flex-shrink: 0;
  opacity: var(--opacity-dot);
}
</style>
