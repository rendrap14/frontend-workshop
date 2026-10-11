<script setup>
const contacts = [
  {
    id: 'whatsapp',
    title: 'WhatsApp',
    handle: '+62 812-9024-9319',
    detail: 'Fast Response via Chat',
    href: 'https://wa.me/qr/UKYJ76TRUFARO1',
    btnText: 'Chat WhatsApp',
    badgeColor: '#25D366',
    iconType: 'whatsapp'
  },
  {
    id: 'instagram',
    title: 'Instagram',
    handle: '@reirend__',
    detail: 'Aktivitas & Keseharian',
    href: 'https://instagram.com/reirend__?obrf=YWt2d3o2MzF0c2Ux',
    btnText: 'Ikuti di Instagram',
    badgeColor: '#E1306C',
    iconType: 'instagram'
  },
  {
    id: 'tiktok',
    title: 'TikTok',
    handle: '@rend_aja14',
    detail: 'Video Kreatif & Edukasi',
    href: 'https://www.tiktok.com/@rend_aja14?is_from_webapp=1&sender_device=pc',
    btnText: 'Tonton di TikTok',
    badgeColor: '#111111',
    iconType: 'tiktok'
  },
  {
    id: 'gmaps',
    title: 'Lokasi',
    handle: 'Universitas PGRI Semarang',
    detail: 'Jawa Tengah, Indonesia',
    href: 'https://maps.app.goo.gl/kTswBr1SPnM8RHC58',
    btnText: 'Buka Google Maps',
    badgeColor: '#EA4335',
    iconType: 'gmaps'
  }
]
</script>

<template>
  <section id="kontak" class="contact-section">
    <div class="contact-container">
      <!-- Header Section -->
      <div class="section-header">
        <h2 class="section-title">Kontak</h2>
        <p class="section-subtitle">
          Mari terhubung dan berkolaborasi. Anda dapat menghubungi saya melalui media sosial atau tautan di bawah ini.
        </p>
      </div>

      <!-- Grid Kartu Kontak -->
      <div class="contact-grid">
        <div v-for="item in contacts" :key="item.id" class="contact-card">
          <div class="card-icon-wrapper" :style="{ backgroundColor: item.badgeColor + '18' }">
            <!-- SVG Icons -->
            <svg
              v-if="item.iconType === 'whatsapp'"
              xmlns="http://www.w3.org/2000/svg"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="currentColor"
              :style="{ color: item.badgeColor }"
            >
              <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766 0-3.18-2.586-5.771-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.069-.252-.08-.575-.187-.988-.365-1.739-.751-2.874-2.502-2.961-2.617-.087-.116-.708-.94-.708-1.793s.448-1.273.607-1.446c.159-.173.346-.217.462-.217l.332.006c.106.005.249-.04.39.298.144.347.491 1.2.534 1.287.043.087.072.188.014.304-.058.116-.087.188-.173.289l-.26.304c-.087.086-.177.18-.076.354.101.174.449.741.964 1.201.662.591 1.221.774 1.394.86.173.086.275.072.376-.044.101-.116.433-.506.549-.68.116-.173.231-.145.39-.087s1.011.477 1.184.564.289.13.332.202c.043.073.043.419-.101.824z" />
            </svg>

            <svg
              v-else-if="item.iconType === 'instagram'"
              xmlns="http://www.w3.org/2000/svg"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="currentColor"
              :style="{ color: item.badgeColor }"
            >
              <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z" />
            </svg>

            <svg
              v-else-if="item.iconType === 'tiktok'"
              xmlns="http://www.w3.org/2000/svg"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="currentColor"
              :style="{ color: item.badgeColor }"
            >
              <path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64c.29 0 .57.04.84.11V9.32a6.33 6.33 0 0 0-.84-.06 6.34 6.34 0 0 0-6.34 6.34 6.34 6.34 0 0 0 6.34 6.34 6.34 6.34 0 0 0 6.34-6.34V8.75c1.45 1.04 3.23 1.66 5.16 1.71V7a4.87 4.87 0 0 1-1.39-.31z" />
            </svg>

            <svg
              v-else-if="item.iconType === 'gmaps'"
              xmlns="http://www.w3.org/2000/svg"
              width="28"
              height="28"
              viewBox="0 0 24 24"
              fill="currentColor"
              :style="{ color: item.badgeColor }"
            >
              <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z" />
            </svg>
          </div>

          <div class="card-info">
            <span class="card-platform">{{ item.title }}</span>
            <h3 class="card-handle">{{ item.handle }}</h3>
            <p class="card-detail">{{ item.detail }}</p>
          </div>

          <a
            :href="item.href"
            target="_blank"
            rel="noopener noreferrer"
            class="card-btn"
          >
            {{ item.btnText }} &rarr;
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  position: relative;
  width: 100%;
  padding: 95px 24px 85px;
  background: radial-gradient(circle at 50% 40%, #e3e6eb 0%, #cbd0d6 75%, #bcc1c8 100%);
  box-sizing: border-box;
}

.contact-container {
  max-width: 1140px;
  margin: 0 auto;
}

/* Header Section */
.section-header {
  text-align: center;
  margin-bottom: 56px;
}

.section-title {
  margin: 0 0 12px 0;
  font-size: 52px;
  font-weight: 800;
  color: #262933;
  letter-spacing: -0.02em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.section-subtitle {
  margin: 0 auto;
  font-size: 18px;
  line-height: 1.6;
  color: #4b5262;
  max-width: 620px;
}

/* Grid Kartu Kontak */
.contact-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
  margin-bottom: 0;
}

.contact-card {
  background: #ffffff;
  border-radius: 16px;
  padding: 32px 24px 28px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.6);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.3s ease;
}

.contact-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 18px 36px rgba(0, 0, 0, 0.15);
}

.card-icon-wrapper {
  width: 60px;
  height: 60px;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  transition: transform 0.3s ease;
}

.contact-card:hover .card-icon-wrapper {
  transform: scale(1.1);
}

.card-info {
  margin-bottom: 24px;
  flex-grow: 1;
}

.card-platform {
  display: inline-block;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #8b92a0;
  margin-bottom: 6px;
}

.card-handle {
  margin: 0 0 6px 0;
  font-size: 19px;
  font-weight: 800;
  color: #262933;
  line-height: 1.25;
  word-break: break-word;
}

.card-detail {
  margin: 0;
  font-size: 14px;
  color: #555b6e;
}

/* Tombol Kartu */
.card-btn {
  width: 100%;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 11px 20px;
  background-color: #00c9a7;
  color: #ffffff;
  font-size: 14.5px;
  font-weight: 700;
  text-decoration: none;
  border-radius: 999px;
  box-shadow: 0 6px 16px rgba(0, 201, 167, 0.3);
  transition: all 0.25s ease;
  box-sizing: border-box;
}

.card-btn:hover {
  background-color: #00b696;
  box-shadow: 0 8px 22px rgba(0, 201, 167, 0.45);
  transform: translateY(-2px);
}

.card-btn:active {
  transform: translateY(0);
}

/* Responsivitas */
@media (max-width: 1024px) {
  .contact-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
}

@media (max-width: 600px) {
  .contact-section {
    padding: 70px 20px 50px;
  }

  .section-title {
    font-size: 38px;
  }

  .section-subtitle {
    font-size: 16px;
  }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 18px;
  }

  .contact-card {
    padding: 24px 20px;
  }
}
</style>
