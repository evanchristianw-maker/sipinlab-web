<script setup>
import AppIcon from './AppIcon.vue'

defineProps({
  label: {
    type: String,
    default: '',
  },
  value: {
    type: [String, Number],
    default: 0,
  },
  icon: {
    type: String,
    default: '',
  },
  tone: {
    type: String,
    default: 'primary', // primary | success | warning | danger | info
  },
  note: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="stat-card">
    <div class="stat-head">
      <span class="stat-label">{{ label }}</span>
      <span v-if="icon" :class="['stat-icon', `tone-${tone}`]">
        <AppIcon :name="icon" />
      </span>
    </div>
    <div class="stat-value">{{ value }}</div>
    <div v-if="note" class="stat-note">{{ note }}</div>
  </div>
</template>

<style scoped>
.stat-card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
  padding: var(--space-5);
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
}

.stat-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: var(--space-2);
}

.stat-label {
  font-size: var(--font-size-sm);
  font-weight: 600;
  color: var(--color-text-muted);
}

.stat-icon {
  width: 36px;
  height: 36px;
  border-radius: var(--radius-md);
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.tone-primary {
  background: var(--color-primary-soft);
  color: var(--color-primary);
}

.tone-success {
  background: var(--color-success-soft);
  color: var(--color-success);
}

.tone-warning {
  background: var(--color-warning-soft);
  color: var(--color-warning);
}

.tone-danger {
  background: var(--color-danger-soft);
  color: var(--color-danger);
}

.tone-info {
  background: var(--color-info-soft);
  color: var(--color-info);
}

.stat-value {
  font-size: var(--font-size-xl);
  font-weight: 700;
  color: var(--color-text);
  line-height: 1.2;
}

.stat-note {
  font-size: var(--font-size-xs);
  color: var(--color-text-muted);
}
</style>
