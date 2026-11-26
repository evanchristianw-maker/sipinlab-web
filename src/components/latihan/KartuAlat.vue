<script setup>
import { computed } from 'vue'

const props = defineProps({
  kode: { type: String, required: true },
  nama: { type: String, required: true },
  tersedia: { type: Number, default: 0 },
  total: { type: Number, default: 0 },
  kondisi: { type: String, default: 'baik' },
})

const emit = defineEmits(['pinjam', 'kembali'])

const infoKondisi = computed(() => {
  const peta = {
    baik: { teks: 'Baik', kelas: 'kondisi-baik' },
    rusak_ringan: { teks: 'Rusak ringan', kelas: 'kondisi-ringan' },
    rusak_berat: { teks: 'Rusak berat', kelas: 'kondisi-berat' },
  }
  return peta[props.kondisi] ?? { teks: props.kondisi, kelas: 'kondisi-baik' }
})
</script>

<template>
  <article class="kartu" :class="{ habis: tersedia === 0 }">
    <div class="kartu-atas">
      <span class="kode">{{ kode }}</span>
      <span class="badge" :class="infoKondisi.kelas">{{ infoKondisi.teks }}</span>
    </div>
    <h3>{{ nama }}</h3>
    <p>
      Tersedia <strong>{{ tersedia }}</strong> dari {{ total }} unit
    </p>
    <p v-if="tersedia === 0" class="label-habis">Stok habis</p>
    <div class="aksi">
      <button class="btn-pinjam" :disabled="tersedia === 0" @click="emit('pinjam', kode)">
        Pinjam 1 unit
      </button>
      <button class="btn-kembali" :disabled="tersedia >= total" @click="emit('kembali', kode)">
        Kembalikan 1 unit
      </button>
    </div>
  </article>
</template>

<style scoped>
.kartu {
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 16px;
  background: #fff;
  display: flex;
  flex-direction: column;
}
.kartu.habis {
  opacity: 0.75;
}
.kartu-atas {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
}
.kode {
  font-size: 12px;
  color: #64748b;
}
.badge {
  font-size: 11px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 999px;
}
.kondisi-baik {
  background: #dcfce7;
  color: #15803d;
}
.kondisi-ringan {
  background: #fef3c7;
  color: #b45309;
}
.kondisi-berat {
  background: #fee2e2;
  color: #b91c1c;
}
h3 {
  margin: 6px 0 8px;
}
.label-habis {
  color: #b91c1c;
  font-weight: 600;
  margin: 0 0 8px;
}
.aksi {
  margin-top: auto;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
button {
  padding: 8px 12px;
  border: 0;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
}
.btn-pinjam {
  background: #0e7c66;
  color: #fff;
}
.btn-kembali {
  background: #e2e8f0;
  color: #0f172a;
}
button:disabled {
  background: #cbd5e1;
  color: #64748b;
  cursor: not-allowed;
}
</style>
