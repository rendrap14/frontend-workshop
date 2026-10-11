<script setup>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ExperienceDetailSection from './components/ExperienceDetailSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <Header />
  <main>
    <HeroSection />
    <AboutSection />
    <ExperienceSection />
    <ExperienceDetailSection />
    <ContactSection />
  </main>
  <Footer />
</template>

<style scoped>
main {
  width: 100%;
  display: flex;
  flex-direction: column;
}
</style>
