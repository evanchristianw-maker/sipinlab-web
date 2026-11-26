<script setup>
import { ref } from 'vue'
import BaseButton from '@/components/base/BaseButton.vue'
import BaseInput from '@/components/base/BaseInput.vue'
import StatusBadge from '@/components/base/StatusBadge.vue'
import StatCard from '@/components/base/StatCard.vue'

const inputNormal = ref('admin@sipinlab.test')
const inputGalat = ref('bukan-email')
</script>

<template>
  <div class="showcase-page">
    <header class="showcase-header">
      <h1>00 Design System — Komponen Dasar</h1>
      <p>Katalog seluruh varian komponen antarmuka aplikasi SIPINLAB.</p>
    </header>

    <!-- 1. BaseButton -->
    <section class="card">
      <h2>1. BaseButton (Varian & Ukuran)</h2>
      <div class="row">
        <BaseButton variant="primary">Primary</BaseButton>
        <BaseButton variant="secondary">Secondary</BaseButton>
        <BaseButton variant="danger">Danger</BaseButton>
        <BaseButton variant="ghost">Ghost</BaseButton>
        <BaseButton variant="primary" size="sm">Small (sm)</BaseButton>
        <BaseButton variant="primary" loading>Loading</BaseButton>
        <BaseButton variant="primary" disabled>Disabled</BaseButton>
      </div>
      <div class="row" style="margin-top: 12px;">
        <BaseButton variant="primary" block>Block Button (Lebar Penuh)</BaseButton>
      </div>
    </section>

    <!-- 2. BaseInput -->
    <section class="card">
      <h2>2. BaseInput (Normal & Galat)</h2>
      <div class="grid-2">
        <BaseInput
          v-model="inputNormal"
          label="Surel (Normal)"
          type="email"
          placeholder="nama@sipinlab.test"
          hint="Gunakan surel resmi institusi."
          required
        />
        <BaseInput
          v-model="inputGalat"
          label="Surel (Galat / Error)"
          type="email"
          error="Format surel tidak valid."
          required
        />
      </div>
    </section>

    <!-- 3. StatusBadge -->
    <section class="card">
      <h2>3. StatusBadge</h2>
      <div class="row">
        <StatusBadge value="tersedia" />
        <StatusBadge value="disetujui" />
        <StatusBadge value="selesai" />
        <StatusBadge value="baik" />
        <StatusBadge value="dipinjam" />
        <StatusBadge value="menunggu" />
        <StatusBadge value="perawatan" />
        <StatusBadge value="rusak_ringan" />
        <StatusBadge value="ditolak" />
        <StatusBadge value="rusak_berat" />
        <StatusBadge value="lainnya" />
      </div>
    </section>

    <!-- 4. StatCard -->
    <section class="card">
      <h2>4. StatCard</h2>
      <div class="grid-4">
        <StatCard label="Total Alat" value="128" icon="box" tone="primary" note="Semua kategori" />
        <StatCard label="Tersedia" value="94" icon="check" tone="success" note="Siap dipinjam" />
        <StatCard label="Menunggu Persetujuan" value="12" icon="clock" tone="warning" note="Perlu tinjauan" />
        <StatCard label="Rusak Berat" value="4" icon="alert" tone="danger" note="Dalam perbaikan" />
      </div>
    </section>
  </div>
</template>

<style scoped>
.showcase-page {
  max-width: 1120px;
  margin: 0 auto;
  padding: var(--space-6) var(--space-5);
  display: flex;
  flex-direction: column;
  gap: var(--space-5);
}

.showcase-header h1 {
  font-size: var(--font-size-xl);
  color: var(--color-text);
}

.showcase-header p {
  margin: 4px 0 0;
  color: var(--color-text-muted);
  font-size: var(--font-size-sm);
}

.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-5);
  box-shadow: var(--shadow-sm);
}

.card h2 {
  font-size: var(--font-size-md);
  margin-bottom: var(--space-4);
  color: var(--color-text);
}

.row {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: var(--space-3);
}

.grid-2 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-4);
}

.grid-4 {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--space-4);
}

@media (max-width: 860px) {
  .grid-2,
  .grid-4 {
    grid-template-columns: 1fr;
  }
}
</style>