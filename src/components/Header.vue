<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import rinfoLogo from '../assets/rinfo-logo.png'

const isScrolled = ref(false)
const activeMenu = ref('Beranda')
const isMobileMenuOpen = ref(false)

const navMenus = [
  { name: 'Beranda', href: '#beranda' },
  { name: 'Tentang', href: '#tentang' },
  { name: 'Foto', href: '#foto' },
  { name: 'Pengalaman', href: '#pengalaman' },
  { name: 'Kontak', href: '#kontak' }
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}

const setActive = (name) => {
  activeMenu.value = name
  isMobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header class="site-header" :class="{ 'is-scrolled': isScrolled }">
    <div class="header-container">
      <!-- Logo Kiri -->
      <a href="#beranda" class="logo" @click="setActive('Beranda')">
        <img :src="rinfoLogo" alt="RINFO Logo" class="logo-image" />
      </a>

      <!-- 5 Menu Kanan (Desktop) -->
      <nav class="nav-desktop" aria-label="Navigasi Utama">
        <ul class="nav-list">
          <li v-for="menu in navMenus" :key="menu.name" class="nav-item">
            <a
              :href="menu.href"
              class="nav-link"
              :class="{ 'is-active': activeMenu === menu.name }"
              @click="setActive(menu.name)"
            >
              {{ menu.name }}
              <span v-if="activeMenu === menu.name" class="active-indicator"></span>
            </a>
          </li>
        </ul>
      </nav>

      <!-- Hamburger Button untuk Layar Mobile -->
      <button
        type="button"
        class="menu-toggle"
        :class="{ 'is-active': isMobileMenuOpen }"
        @click="toggleMobileMenu"
        aria-label="Toggle navigasi"
      >
        <span class="hamburger-bar"></span>
        <span class="hamburger-bar"></span>
        <span class="hamburger-bar"></span>
      </button>
    </div>

    <!-- Dropdown Menu Mobile -->
    <transition name="fade-slide">
      <div v-if="isMobileMenuOpen" class="mobile-nav">
        <ul class="mobile-nav-list">
          <li v-for="menu in navMenus" :key="menu.name">
            <a
              :href="menu.href"
              class="mobile-nav-link"
              :class="{ 'is-active': activeMenu === menu.name }"
              @click="setActive(menu.name)"
            >
              {{ menu.name }}
            </a>
          </li>
        </ul>
      </div>
    </transition>
  </header>
</template>

<style scoped>
/* Sticky / Fixed Header dengan Warna Transparan & Efek Blur saat Scroll */
.site-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 1000;
  background-color: transparent;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

/* Keadaan saat di-scroll: latar semi-transparan dengan blur modern */
.site-header.is-scrolled {
  background-color: rgba(203, 207, 212, 0.85);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.08);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 18px 36px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  transition: padding 0.3s ease;
}

.site-header.is-scrolled .header-container {
  padding: 12px 36px;
}

/* Logo styling */
.logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  cursor: pointer;
  user-select: none;
}

.logo-image {
  height: 48px;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.06));
  transition: transform 0.2s ease;
}

.logo:hover .logo-image {
  transform: scale(1.03);
}

/* Navigasi Desktop */
.nav-desktop {
  display: flex;
  align-items: center;
}

.nav-list {
  display: flex;
  align-items: center;
  gap: 32px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: inline-block;
  padding: 6px 0;
  font-size: 16.5px;
  font-weight: 600;
  color: #4b5262;
  text-decoration: none;
  transition: color 0.2s ease;
  position: relative;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.nav-link:hover {
  color: #1f2937;
}

.nav-link.is-active {
  color: #00c9a7;
  font-weight: 700;
}

.active-indicator {
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 100%;
  height: 3px;
  background-color: #00c9a7;
  border-radius: 4px;
}

/* Mobile Toggle Button */
.menu-toggle {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  width: 40px;
  height: 40px;
  padding: 8px;
  background: rgba(255, 255, 255, 0.4);
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  cursor: pointer;
}

.hamburger-bar {
  display: block;
  width: 100%;
  height: 2px;
  background-color: #222;
  border-radius: 2px;
  transition: transform 0.25s ease, opacity 0.25s ease;
}

.menu-toggle.is-active .hamburger-bar:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}

.menu-toggle.is-active .hamburger-bar:nth-child(2) {
  opacity: 0;
}

.menu-toggle.is-active .hamburger-bar:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

/* Mobile Nav Menu */
.mobile-nav {
  display: none;
  background: rgba(240, 242, 245, 0.96);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.08);
  padding: 16px 24px;
}

.mobile-nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.mobile-nav-link {
  display: block;
  padding: 10px 16px;
  font-size: 16px;
  font-weight: 600;
  color: #4b5262;
  text-decoration: none;
  border-radius: 8px;
  transition: all 0.2s ease;
}

.mobile-nav-link:hover,
.mobile-nav-link.is-active {
  color: #00c9a7;
  background: rgba(0, 201, 167, 0.1);
}

/* Animasi Transition */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.25s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* Responsivitas */
@media (max-width: 820px) {
  .nav-desktop {
    display: none;
  }
  .menu-toggle {
    display: flex;
  }
  .mobile-nav {
    display: block;
  }
}
</style>
