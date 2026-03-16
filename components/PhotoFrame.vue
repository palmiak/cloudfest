<script setup lang="ts">
interface Props {
  src?: string
  alt?: string
}

defineProps<Props>()
</script>

<template>
  <div class="photo-frame">
    <img v-if="src" :src="src" :alt="alt" class="photo-image" />
    <div v-else class="photo-placeholder">
      Photo<br>Placeholder
    </div>
  </div>
</template>

<style scoped>
.photo-frame {
  width: var(--photo-frame-size);
  height: var(--photo-frame-size);
  border-radius: 50%;
  border: 2px solid rgba(175, 230, 20, 0.3);
  background: var(--color-bg-subtle);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  margin-right: 7%;
}

.photo-image {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
}

.photo-placeholder {
  font-size: clamp(8px, 0.9vw, 10px);
  color: rgba(255, 255, 255, 0.2);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  text-align: center;
  line-height: 1.6;
}
</style>
