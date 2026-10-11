<script setup>
import { ref } from 'vue'
import profileImg from '../assets/profile.png'
import kegiatan1 from '../assets/kegiatan 1.png'
import kegiatan2 from '../assets/kegiatan 2.png'
import kegiatan3 from '../assets/kegiatan 3.png'

const activeDot = ref(1)

const activities = [
  { id: 0, img: kegiatan1, alt: 'Kegiatan Kampus 1' },
  { id: 1, img: kegiatan2, alt: 'Juara 1 Kompetisi Kegiatan 2' },
  { id: 2, img: kegiatan3, alt: 'Seminar dan Perkuliahan Kegiatan 3' }
]
</script>

<template>
  <section id="beranda" class="hero-section">
    <!-- Bagian Atas: Profil Utama -->
    <div class="hero-container">
      <!-- Kolom Kiri: Foto Profil -->
      <div class="hero-image-wrapper">
        <div class="image-glow"></div>
        <img
          :src="profileImg"
          alt="Carendra Rendra Aldiansyah"
          class="hero-profile-img"
        />
      </div>

      <!-- Kolom Kanan: Teks & Informasi -->
      <div class="hero-content">
        <div class="hero-name-group">
          <div class="name-first-row">
            <h1 class="hero-first-name">Carendra</h1>
            <div class="nickname-badge">
              <span>Rendra</span>
            </div>
          </div>
          <h2 class="hero-last-name">Aldiansyah</h2>
        </div>

        <p class="hero-description">
          Saya merupakan mahasiswa UPGRIS dari program studi Informatika angkatan tahun 2024
        </p>

        <div class="hero-actions">
          <a href="#tentang" class="btn-about">
            Tentang Saya
          </a>
        </div>
      </div>
    </div>

    <!-- Bagian Bawah: Foto Beberapa Kegiatan -->
    <div class="activities-wrapper">
      <div class="activities-header">
        <h2 class="activities-title">Foto Beberapa Kegiatan</h2>
        <p class="activities-subtitle">
          Foto di bawah merupakan sebagian kegiatan yan pernah saya ikuti selama 2 tahun belakangan ini ketika kuliah di UPGIS
        </p>
      </div>

      <!-- Grid 3 Foto Kegiatan -->
      <div class="activities-grid">
        <div
          v-for="(item, index) in activities"
          :key="item.id"
          class="activity-card"
          @click="activeDot = index"
        >
          <img :src="item.img" :alt="item.alt" class="activity-img" />
        </div>
      </div>

      <!-- Dots Indikator -->
      <div class="dots-indicator">
        <span
          v-for="i in [0, 1, 2]"
          :key="i"
          class="dot"
          :class="{ 'is-active': activeDot === i }"
          @click="activeDot = i"
        ></span>
      </div>

      <!-- Tombol Mengarah ke Section Pengalaman -->
      <div class="activities-action">
        <a href="#foto" class="btn-more-photos">
          Foto lainya
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 110px 24px 70px;
  background: radial-gradient(circle at 50% 30%, #e3e6eb 0%, #cbd0d6 75%, #bcc1c8 100%);
  box-sizing: border-box;
  overflow: hidden;
}

.hero-container {
  max-width: 1140px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 50px;
}

/* Kolom Kiri: Foto Profil */
.hero-image-wrapper {
  position: relative;
  flex: 0 0 auto;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.image-glow {
  position: absolute;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(0, 196, 159, 0.15) 0%, rgba(255, 255, 255, 0) 70%);
  border-radius: 50%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  filter: blur(30px);
  z-index: 1;
  pointer-events: none;
}

.hero-profile-img {
  position: relative;
  z-index: 2;
  width: 290px;
  height: auto;
  max-height: 440px;
  object-fit: contain;
  filter: drop-shadow(0 15px 30px rgba(0, 0, 0, 0.18));
  transition: transform 0.35s ease, filter 0.35s ease;
}

.hero-profile-img:hover {
  transform: translateY(-4px) scale(1.02);
  filter: drop-shadow(0 20px 35px rgba(0, 0, 0, 0.22));
}

/* Kolom Kanan: Teks & Informasi */
.hero-content {
  flex: 1 1 500px;
  max-width: 620px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  text-align: left;
}

.hero-name-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

.name-first-row {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

.hero-first-name {
  margin: 0;
  font-size: 58px;
  font-weight: 800;
  color: #262933;
  line-height: 1.1;
  letter-spacing: -0.03em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

/* Badge Miring "Rendra" */
.nickname-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background-color: #00c9a7;
  color: #ffffff;
  padding: 8px 24px;
  border-radius: 28px;
  transform: rotate(-6deg);
  box-shadow: 0 8px 18px rgba(0, 201, 167, 0.35);
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  user-select: none;
}

.nickname-badge:hover {
  transform: rotate(-3deg) scale(1.08);
}

.nickname-badge span {
  font-size: 34px;
  font-weight: 800;
  letter-spacing: -0.01em;
  line-height: 1.1;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.hero-last-name {
  margin: 6px 0 0 0;
  font-size: 58px;
  font-weight: 800;
  color: #262933;
  line-height: 1.1;
  letter-spacing: -0.03em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

/* Deskripsi */
.hero-description {
  margin: 0 0 32px 0;
  font-size: 19px;
  line-height: 1.55;
  color: #4b5262;
  font-weight: 400;
  max-width: 500px;
}

/* Tombol CTA "Tentang Saya" */
.hero-actions {
  display: flex;
  align-items: center;
}

.btn-about {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 13px 36px;
  background-color: #00c9a7;
  color: #ffffff;
  font-size: 16px;
  font-weight: 700;
  text-decoration: none;
  border-radius: 999px;
  box-shadow: 0 8px 20px rgba(0, 201, 167, 0.35);
  transition: all 0.25s ease;
  letter-spacing: -0.01em;
}

.btn-about:hover {
  background-color: #00b696;
  transform: translateY(-2px);
  box-shadow: 0 12px 24px rgba(0, 201, 167, 0.45);
}

.btn-about:active {
  transform: translateY(0);
}

/* ======================================================== */
/* Bagian Bawah: Foto Beberapa Kegiatan                    */
/* ======================================================== */
.activities-wrapper {
  width: 100%;
  max-width: 1140px;
  margin-top: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.activities-header {
  margin-bottom: 36px;
}

.activities-title {
  margin: 0 0 12px 0;
  font-size: 38px;
  font-weight: 800;
  color: #262933;
  letter-spacing: -0.02em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.activities-subtitle {
  margin: 0 auto;
  max-width: 650px;
  font-size: 17.5px;
  line-height: 1.5;
  color: #555b6e;
  font-weight: 400;
}

/* Grid 3 Foto */
.activities-grid {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-bottom: 24px;
}

.activity-card {
  position: relative;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
  background-color: #d1d5db;
  aspect-ratio: 4 / 5;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.activity-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 18px 36px rgba(0, 0, 0, 0.2);
}

.activity-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease;
}

.activity-card:hover .activity-img {
  transform: scale(1.04);
}

/* Dots Indikator */
.dots-indicator {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin-bottom: 28px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid #00c9a7;
  background-color: transparent;
  cursor: pointer;
  transition: all 0.25s ease;
}

.dot.is-active {
  background-color: #00c9a7;
  transform: scale(1.15);
}

/* Tombol Foto Lainya */
.activities-action {
  display: flex;
  justify-content: center;
}

.btn-more-photos {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 13px 40px;
  background-color: #00c9a7;
  color: #ffffff;
  font-size: 16px;
  font-weight: 700;
  text-decoration: none;
  border-radius: 999px;
  box-shadow: 0 8px 20px rgba(0, 201, 167, 0.35);
  transition: all 0.25s ease;
  letter-spacing: -0.01em;
}

.btn-more-photos:hover {
  background-color: #00b696;
  transform: translateY(-2px);
  box-shadow: 0 12px 24px rgba(0, 201, 167, 0.45);
}

.btn-more-photos:active {
  transform: translateY(0);
}

/* ======================================================== */
/* Responsivitas: Tablet & Mobile                           */
/* ======================================================== */
@media (max-width: 900px) {
  .hero-container {
    flex-direction: column;
    text-align: center;
    gap: 36px;
  }

  .hero-content {
    align-items: center;
    text-align: center;
  }

  .name-first-row {
    justify-content: center;
  }

  .hero-profile-img {
    width: 230px;
  }

  .hero-first-name,
  .hero-last-name {
    font-size: 44px;
  }

  .nickname-badge span {
    font-size: 26px;
  }

  .hero-description {
    font-size: 17px;
  }

  .activities-title {
    font-size: 30px;
  }

  .activities-subtitle {
    font-size: 15.5px;
  }

  .activities-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }
}

@media (max-width: 640px) {
  .hero-first-name,
  .hero-last-name {
    font-size: 34px;
  }

  .nickname-badge {
    padding: 6px 18px;
  }

  .nickname-badge span {
    font-size: 22px;
  }

  .hero-profile-img {
    width: 190px;
  }

  .hero-description {
    font-size: 15px;
  }

  .btn-about,
  .btn-more-photos {
    width: 100%;
    padding: 12px 24px;
  }

  .activities-grid {
    grid-template-columns: 1fr;
    gap: 18px;
  }

  .activity-card {
    aspect-ratio: 16 / 10;
  }
}
</style>
