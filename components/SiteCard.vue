<script setup lang="ts">
interface Props {
  iconType: 'active' | 'muted'
  url: string
  description: string
  tag: string
  tagType: 'green' | 'muted'
  urlMuted?: boolean
}

withDefaults(defineProps<Props>(), {
  urlMuted: false
})
</script>

<template>
  <div class="site-card">
    <div class="site-icon" :class="{ 'site-icon-muted': iconType === 'muted' }">
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
        <circle cx="10" cy="10" r="6" :fill="iconType === 'active' ? 'var(--color-green)' : 'rgba(255,255,255,0.2)'" opacity="0.4"/>
      </svg>
    </div>
    <div style="flex: 1;">
      <div class="site-url" :class="{ 'site-url-muted': urlMuted }">{{ url }}</div>
      <div class="site-desc">{{ description }}</div>
    </div>
    <div class="tag" :class="`tag-${tagType}`">{{ tag }}</div>
  </div>
</template>

<style scoped>
.site-card {
  background: var(--color-bg-subtle);
  border: 0.5px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--padding-card);
  display: flex;
  align-items: center;
  gap: var(--gap-card);
}

.site-icon {
  width: var(--icon-size);
  height: var(--icon-size);
  border-radius: var(--radius-md);
  background: rgba(175, 230, 20, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.site-icon-muted {
  background: var(--color-bg-muted);
}

.site-url {
  font-size: var(--font-size-small);
  font-weight: 400;
  color: var(--color-text-primary);
}

.site-url-muted {
  color: var(--color-text-dim);
}

.site-desc {
  font-size: var(--font-size-tiny);
  color: var(--color-text-muted);
  font-weight: 300;
  margin-top: 2px;
}

/* Tag styles inherited from global index.css */
</style>
