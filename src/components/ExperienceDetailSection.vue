<script setup>
import { ref } from 'vue'
import arakarakanVideo from '../assets/arakarakan.mp4'

const videoRef = ref(null)
</script>

<template>
  <section id="pengalaman" class="experience-detail-section">
    <div class="section-container">
      <!-- Kolom Kiri: Teks Pengalaman & Tombol Kontak -->
      <div class="content-col">
        <h2 class="section-title">Pengalaman</h2>
        <p class="section-description">
          Saya memiliki pengalaman mengembangkan website menggunakan HTML, CSS, dan JavaScript, membangun aplikasi mobile menggunakan Flutter, serta mengerjakan proyek berbasis Python dan Flask. Selain itu, saya aktif dalam organisasi BEM Fakultas Teknik dan Informatika (FTI), yang membantu saya mengembangkan kemampuan kerja sama tim, komunikasi, dan organisasi.
        </p>

        <div class="action-wrapper">
          <a href="#kontak" class="btn-contact">
            Kontak <span class="arrow">&rarr;</span>
          </a>
        </div>
      </div>

      <!-- Kolom Kanan: Pemutar Video -->
      <div class="video-col">
        <div class="video-card">
          <video
            ref="videoRef"
            :src="arakarakanVideo"
            class="experience-video"
            controls
            autoplay
            loop
            muted
            playsinline
          >
            Browser Anda tidak mendukung tag video.
          </video>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-detail-section {
  position: relative;
  width: 100%;
  min-height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 90px 24px 100px;
  background: radial-gradient(circle at 50% 50%, #e3e6eb 0%, #cbd0d6 75%, #bcc1c8 100%);
  box-sizing: border-box;
}

.section-container {
  max-width: 1140px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 60px;
}

/* Kolom Kiri: Teks */
.content-col {
  flex: 1 1 500px;
  max-width: 540px;
  text-align: left;
}

.section-title {
  margin: 0 0 24px 0;
  font-size: 52px;
  font-weight: 800;
  color: #262933;
  line-height: 1.15;
  letter-spacing: -0.03em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.section-description {
  margin: 0 0 36px 0;
  font-size: 18.5px;
  line-height: 1.65;
  color: #4b5262;
  font-weight: 400;
  text-align: justify;
}

/* Tombol Kontak */
.action-wrapper {
  display: flex;
  align-items: center;
}

.btn-contact {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 13px 36px;
  background-color: #00c9a7;
  color: #ffffff;
  font-size: 16.5px;
  font-weight: 700;
  text-decoration: none;
  border-radius: 999px;
  box-shadow: 0 8px 20px rgba(0, 201, 167, 0.35);
  transition: all 0.25s ease;
  letter-spacing: -0.01em;
}

.btn-contact:hover {
  background-color: #00b696;
  transform: translateY(-2px);
  box-shadow: 0 12px 24px rgba(0, 201, 167, 0.45);
}

.btn-contact:active {
  transform: translateY(0);
}

.arrow {
  font-size: 18px;
  transition: transform 0.2s ease;
}

.btn-contact:hover .arrow {
  transform: translateX(4px);
}

/* Kolom Kanan: Video */
.video-col {
  flex: 1 1 500px;
  max-width: 560px;
  display: flex;
  justify-content: center;
}

.video-card {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.16);
  background-color: #1f2937;
  aspect-ratio: 16 / 10;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.35s ease, box-shadow 0.35s ease;
}

.video-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.22);
}

.experience-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Responsivitas: Tablet & Mobile */
@media (max-width: 960px) {
  .section-container {
    flex-direction: column-reverse;
    text-align: center;
    gap: 48px;
  }

  .content-col {
    max-width: 600px;
    text-align: center;
  }

  .section-title {
    font-size: 40px;
    margin-bottom: 18px;
  }

  .section-description {
    font-size: 17px;
    text-align: center;
    margin-bottom: 28px;
  }

  .action-wrapper {
    justify-content: center;
  }

  .video-col {
    max-width: 100%;
    width: 100%;
  }

  .video-card {
    max-width: 540px;
  }
}

@media (max-width: 520px) {
  .experience-detail-section {
    padding: 60px 20px 80px;
  }

  .section-title {
    font-size: 34px;
  }

  .section-description {
    font-size: 15.5px;
    line-height: 1.6;
  }

  .btn-contact {
    width: 100%;
    justify-content: center;
    padding: 12px 24px;
  }

  .video-card {
    aspect-ratio: 16 / 11;
  }
}
</style>
