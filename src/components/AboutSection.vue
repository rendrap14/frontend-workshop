<script setup>
import nengokImg from '../assets/nengok.png'
</script>

<template>
  <section id="tentang" class="about-section">
    <div class="about-container">
      <!-- Kolom Kiri: Teks Tentang Saya -->
      <div class="about-content">
        <h2 class="about-title">Tentang Saya?</h2>
        <p class="about-description">
          Saya adalah mahasiswa Informatika Universitas PGRI Semarang angkatan 2024 yang memiliki minat dalam Web Development dan Mobile App Development. Saya terus mengembangkan keterampilan pemrograman dan desain aplikasi melalui berbagai proyek, serta berkomitmen untuk belajar, berinovasi, dan menciptakan solusi digital yang bermanfaat.
        </p>
      </div>

      <!-- Kolom Kanan: Foto dan Elemen Geometris -->
      <div class="about-image-wrapper">
        <!-- Bentuk Geometris Miring di Belakang Foto -->
        <div class="geometric-shape"></div>
        <!-- Foto nengok.png -->
        <img
          :src="nengokImg"
          alt="Carendra Rendra - Tentang Saya"
          class="about-img"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  position: relative;
  width: 100%;
  min-height: 85vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 24px 100px;
  background: radial-gradient(circle at 45% 50%, #e3e6eb 0%, #cbd0d6 75%, #bcc1c8 100%);
  box-sizing: border-box;
  overflow: hidden;
}

.about-container {
  max-width: 1140px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 60px;
}

/* Kolom Kiri: Teks */
.about-content {
  flex: 1 1 520px;
  max-width: 560px;
  text-align: left;
}

.about-title {
  margin: 0 0 24px 0;
  font-size: 52px;
  font-weight: 800;
  color: #262933;
  line-height: 1.15;
  letter-spacing: -0.03em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.about-description {
  margin: 0;
  font-size: 19px;
  line-height: 1.68;
  color: #4b5262;
  font-weight: 400;
  text-align: justify;
}

/* Kolom Kanan: Foto & Bentuk Geometris */
.about-image-wrapper {
  position: relative;
  flex: 0 0 auto;
  width: 440px;
  height: 520px;
  display: flex;
  align-items: flex-end;
  justify-content: center;
}

/* Bidang Geometris Miring di Belakang Foto */
.geometric-shape {
  position: absolute;
  right: 10px;
  bottom: 30px;
  width: 320px;
  height: 420px;
  background: rgba(162, 170, 182, 0.45);
  clip-path: polygon(0% 32%, 100% 8%, 100% 100%, 0% 100%);
  border-radius: 4px;
  z-index: 1;
  pointer-events: none;
  transition: transform 0.35s ease, background-color 0.35s ease;
}

.about-image-wrapper:hover .geometric-shape {
  transform: scale(1.02) translate(4px, -4px);
  background: rgba(162, 170, 182, 0.55);
}

/* Foto nengok.png */
.about-img {
  position: relative;
  z-index: 2;
  height: 500px;
  width: auto;
  max-width: 100%;
  object-fit: contain;
  filter: drop-shadow(0 15px 30px rgba(0, 0, 0, 0.16));
  transition: transform 0.35s ease, filter 0.35s ease;
}

.about-img:hover {
  transform: translateY(-5px) scale(1.02);
  filter: drop-shadow(0 20px 35px rgba(0, 0, 0, 0.22));
}

/* Responsivitas: Tablet & Mobile */
@media (max-width: 960px) {
  .about-container {
    flex-direction: column-reverse;
    text-align: center;
    gap: 48px;
  }

  .about-content {
    text-align: center;
    max-width: 620px;
  }

  .about-title {
    font-size: 42px;
    margin-bottom: 20px;
  }

  .about-description {
    font-size: 17.5px;
    text-align: center;
  }

  .about-image-wrapper {
    width: 360px;
    height: 440px;
  }

  .about-img {
    height: 420px;
  }

  .geometric-shape {
    width: 260px;
    height: 350px;
  }
}

@media (max-width: 520px) {
  .about-section {
    padding: 60px 20px 80px;
  }

  .about-title {
    font-size: 34px;
  }

  .about-description {
    font-size: 15.5px;
    line-height: 1.6;
  }

  .about-image-wrapper {
    width: 280px;
    height: 360px;
  }

  .about-img {
    height: 340px;
  }

  .geometric-shape {
    width: 200px;
    height: 280px;
    clip-path: polygon(0% 30%, 100% 10%, 100% 100%, 0% 100%);
  }
}
</style>
