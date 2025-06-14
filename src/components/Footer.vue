<template>
  <footer class="portfolio-footer">
    <div class="footer-inner">
      <div class="footer-socials">
        <a href="https://github.com/your-github" target="_blank" aria-label="GitHub"><i class="icon-github"></i></a>
        <a href="https://linkedin.com/in/your-linkedin" target="_blank" aria-label="LinkedIn"><i class="icon-linkedin"></i></a>
        <a href="mailto:your@email.com" aria-label="Email"><i class="icon-mail"></i></a>
      </div>
      <div class="footer-copy">© 2025 Nguyen Van FE. All rights reserved.</div>
    </div>
  </footer>
</template>

<script setup lang="ts">
// Không cần logic đặc biệt
</script>

<style scoped lang="scss">
.portfolio-footer {
  width: 100vw;
  background: #fff;
  border-top: 2px solid var(--color-border);
  box-shadow: 0 -2px 12px #7f5fff08;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  z-index: 10;
}
.footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 2rem;
  font-size: 1.05rem;
  color: var(--color-subtext);
}
.footer-socials {
  display: flex;
  gap: 1.2em;
  margin-bottom: 0;
}
.footer-socials a {
  color: var(--color-primary);
  font-size: 1.5em;
  transition: color 0.18s, text-shadow 0.18s;
}
.footer-socials a:hover {
  color: var(--color-accent);
  text-shadow: 0 2px 12px #00e0ff55;
}
.footer-copy {
  font-size: 0.98em;
  color: var(--color-subtext);
}
</style> 