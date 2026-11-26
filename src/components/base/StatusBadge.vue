<script setup>
import { computed } from 'vue'

const props = defineProps({
  value: {
    type: String,
    default: '',
  },
})

const config = computed(() => {
  const val = String(props.value || '').toLowerCase()
  const map = {
    tersedia: { label: 'Tersedia', tone: 'success' },
    disetujui: { label: 'Disetujui', tone: 'success' },
    selesai: { label: 'Selesai', tone: 'success' },
    baik: { label: 'Baik', tone: 'success' },
    dipinjam: { label: 'Dipinjam', tone: 'info' },
    menunggu: { label: 'Menunggu', tone: 'warning' },
    perawatan: { label: 'Perawatan', tone: 'warning' },
    rusak_ringan: { label: 'Rusak Ringan', tone: 'warning' },
    ditolak: { label: 'Ditolak', tone: 'danger' },
    rusak_berat: { label: 'Rusak Berat', tone: 'danger' },
  }
  return map[val] || { label: props.value || '-', tone: 'neutral' }
})
</script>

<template>
  <span :class="['badge', `badge-${config.tone}`]">
    {{ config.label }}
  </span>
</template>

<style scoped>
.badge {
  display: inline-flex;
  align-items: center;
  padding: 2px var(--space-3);
  border-radius: 999px;
  font-size: var(--font-size-xs);
  font-weight: 600;
  line-height: 1.4;
  white-space: nowrap;
}

.badge-neutral {
  background: var(--color-bg);
  color: var(--color-text-muted);
}

.badge-success {
  background: var(--color-success-soft);
  color: var(--color-success);
}

.badge-warning {
  background: var(--color-warning-soft);
  color: var(--color-warning);
}

.badge-danger {
  background: var(--color-danger-soft);
  color: var(--color-danger);
}

.badge-info {
  background: var(--color-info-soft);
  color: var(--color-info);
}
</style>
