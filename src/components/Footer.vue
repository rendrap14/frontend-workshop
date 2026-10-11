<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="site-footer">
    <div class="footer-container">
      <p class="footer-copyright">
        &copy; {{ currentYear }} Carendra Aldiansyah. All rights reserved.
      </p>
      <p class="footer-brand">
        Informatika UPGRIS &bull; RINFO Data Security &amp; System Integrity
      </p>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  width: 100%;
  padding: 40px 24px 45px;
  background: radial-gradient(circle at 50% 0%, #cbd0d6 0%, #c4c9d0 100%);
  border-top: 1px solid rgba(0, 0, 0, 0.06);
  box-sizing: border-box;
  text-align: center;
}

.footer-container {
  max-width: 1140px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.footer-copyright {
  margin: 0;
  font-size: 15px;
  font-weight: 600;
  color: #374151;
  letter-spacing: -0.01em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.footer-brand {
  margin: 0;
  font-size: 13.5px;
  font-weight: 400;
  color: #6b7280;
  letter-spacing: 0.01em;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

@media (max-width: 600px) {
  .site-footer {
    padding: 32px 16px 36px;
  }

  .footer-copyright {
    font-size: 14px;
  }

  .footer-brand {
    font-size: 12.5px;
  }
}
</style>
