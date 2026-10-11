<script setup>
import { ref } from 'vue'
import pengalaman1 from '../assets/pengalaman 1.png'
import pengalaman2 from '../assets/pengalaman 2.png'
import pengalaman3 from '../assets/pengalaman 3.png'
import pengalaman4 from '../assets/pengalaman 4.png'

const experiences = [
  {
    id: 1,
    title: 'Data Utama Net',
    year: '2023',
    img: pengalaman1,
    description: 'Magang di PT. Data Utama Net Semarang selama 6 bulan sebagai teknisi lapangan'
  },
  {
    id: 2,
    title: 'Indihome',
    year: '2024',
    img: pengalaman2,
    description: 'Sertifikasi dan pelatihan keselamatan kerja serta teknis lapangan'
  },
  {
    id: 3,
    title: 'Just Fluf',
    year: '2025',
    img: pengalaman3,
    description: 'PartTime di PT. JustFluff selama kurang lebih 1 tahun'
  },
  {
    id: 4,
    title: 'BEM FTI',
    year: '2026',
    img: pengalaman4,
    description: 'Aktivitas pengurus Badan Eksekutif Mahasiswa Fakultas Teknik dan Informatika UPGRIS'
  }
]

const selectedImage = ref(null)

const openModal = (exp) => {
  selectedImage.value = exp
}

const closeModal = () => {
  selectedImage.value = null
}
</script>

<template>
  <section id="foto" class="experience-section">

    <div class="experience-container">
      <!-- Header Section -->
      <div class="section-header">
        <h2 class="section-title">Foto Pengalaman</h2>
        <p class="section-subtitle">
          Dokumentasi kegiatan dan organisasi dari tahun 2023 - 2026
        </p>
      </div>

      <!-- Grid Kartu Foto Pengalaman -->
      <div class="cards-grid">
        <div
          v-for="item in experiences"
          :key="item.id"
          class="experience-card"
          @click="openModal(item)"
        >
          <div class="card-image-box">
            <img :src="item.img" :alt="item.title" class="card-img" />
            <div class="card-overlay">
              <span class="overlay-icon">🔍 Lihat Detail</span>
            </div>
          </div>
          <div class="card-body">
            <h3 class="card-title">{{ item.title }}</h3>
            <span class="card-year">{{ item.year }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal Lightbox Pop-up -->
    <transition name="modal-fade">
      <div v-if="selectedImage" class="modal-backdrop" @click="closeModal">
        <div class="modal-content" @click.stop>
          <button class="modal-close" @click="closeModal" aria-label="Tutup">×</button>
          <img :src="selectedImage.img" :alt="selectedImage.title" class="modal-img" />
          <div class="modal-info">
            <h3>{{ selectedImage.title }} ({{ selectedImage.year }})</h3>
            <p>{{ selectedImage.description }}</p>
          </div>
        </div>
      </div>
    </transition>
  </section>
</template>

<style scoped>
.experience-section {
  position: relative;
  width: 100%;
  padding: 90px 24px 110px;
  background: radial-gradient(circle at 50% 30%, #e3e6eb 0%, #cbd0d6 75%, #bcc1c8 100%);
  box-sizing: border-box;
}

.section-anchor {
  position: absolute;
  top: -80px;
  left: 0;
}

.experience-container {
  max-width: 1140px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 50px;
}

.section-title {
  margin: 0 0 10px 0;
  font-size: 42px;
  font-weight: 800;
  color: #262933;
  letter-spacing: -0.02em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.section-subtitle {
  margin: 0 auto;
  font-size: 18px;
  color: #555b6e;
  max-width: 600px;
}

/* Grid Kartu */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

/* Kartu Pengalaman */
.experience-card {
  background: #ffffff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.3s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
}

.experience-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 18px 35px rgba(0, 0, 0, 0.15);
}

.card-image-box {
  position: relative;
  width: 100%;
  aspect-ratio: 1 / 1;
  overflow: hidden;
  background-color: #e5e7eb;
}

.card-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease;
}

.experience-card:hover .card-img {
  transform: scale(1.06);
}

.card-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.35);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.25s ease;
}

.experience-card:hover .card-overlay {
  opacity: 1;
}

.overlay-icon {
  color: #ffffff;
  font-size: 14px;
  font-weight: 700;
  background: rgba(0, 201, 167, 0.9);
  padding: 6px 14px;
  border-radius: 999px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.card-body {
  padding: 18px 16px 20px;
  text-align: center;
  background-color: #ffffff;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.card-title {
  margin: 0 0 6px 0;
  font-size: 19px;
  font-weight: 800;
  color: #262933;
  letter-spacing: -0.01em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.card-year {
  font-size: 15px;
  color: #6b7280;
  font-weight: 500;
}

/* Modal Lightbox */
.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.75);
  backdrop-filter: blur(8px);
  z-index: 2000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 24px;
}

.modal-content {
  position: relative;
  background: #ffffff;
  border-radius: 16px;
  overflow: hidden;
  max-width: 720px;
  width: 100%;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.35);
  animation: zoomIn 0.25s ease;
}

.modal-close {
  position: absolute;
  top: 14px;
  right: 14px;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: none;
  background: rgba(0, 0, 0, 0.6);
  color: #ffffff;
  font-size: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
  z-index: 10;
}

.modal-close:hover {
  background: rgba(239, 68, 68, 0.85);
}

.modal-img {
  width: 100%;
  max-height: 500px;
  object-fit: cover;
  display: block;
}

.modal-info {
  padding: 20px 24px;
  text-align: left;
}

.modal-info h3 {
  margin: 0 0 6px;
  font-size: 22px;
  color: #1f2937;
  font-weight: 700;
}

.modal-info p {
  margin: 0;
  color: #4b5563;
  font-size: 15px;
  line-height: 1.5;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.25s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

@keyframes zoomIn {
  from {
    transform: scale(0.92);
  }
  to {
    transform: scale(1);
  }
}

/* Responsivitas */
@media (max-width: 1024px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
}

@media (max-width: 600px) {
  .section-title {
    font-size: 32px;
  }

  .section-subtitle {
    font-size: 16px;
  }

  .cards-grid {
    grid-template-columns: 1fr;
    gap: 18px;
  }

  .experience-card {
    max-width: 360px;
    margin: 0 auto;
    width: 100%;
  }
}
</style>
