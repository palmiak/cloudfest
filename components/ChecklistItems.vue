<script setup lang="ts">
interface CheckItem {
  text: string
  note?: string
}

interface Props {
  items: CheckItem[]
  allVisible?: boolean
}

withDefaults(defineProps<Props>(), {
  allVisible: false
})
</script>

<template>
  <div class="checklist">
    <template v-for="(item, index) in items" :key="index">
      <div v-if="allVisible || index === 0" class="check-item">
        <div class="checkbox">
          <svg class="checkmark" viewBox="0 0 12 12" fill="none">
            <path d="M2 6L5 9L10 3" stroke="var(--color-green)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="check-text">{{ item.text }}</div>
        <div v-if="item.note" class="check-note">{{ item.note }}</div>
      </div>
      <div v-else class="check-item" v-click>
        <div class="checkbox">
          <svg class="checkmark" viewBox="0 0 12 12" fill="none">
            <path d="M2 6L5 9L10 3" stroke="var(--color-green)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="check-text">{{ item.text }}</div>
        <div v-if="item.note" class="check-note">{{ item.note }}</div>
      </div>
    </template>
  </div>
</template>

<style scoped>
.checklist {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

.check-item {
  display: flex;
  align-items: center;
  gap: clamp(10px, 1.4vw, 16px);
  background: rgba(255, 255, 255, 0.03);
  border: 0.5px solid rgba(255, 255, 255, 0.08);
  border-radius: var(--radius-lg);
  padding: var(--padding-check);
}

.checkbox {
  width: var(--checkbox-size);
  height: var(--checkbox-size);
  border-radius: 5px;
  border: 1.5px solid var(--color-green);
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.checkmark {
  width: var(--checkmark-size);
  height: var(--checkmark-size);
}

.check-text {
  font-size: var(--font-size-body);
  color: var(--color-text-primary);
  font-weight: 300;
  flex: 1;
}

.check-note {
  font-size: clamp(8px, 0.85vw, 10px);
  color: var(--color-text-faint);
  font-weight: 300;
  white-space: nowrap;
}
</style>
