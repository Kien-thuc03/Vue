<template>
  <header class="portfolio-header">
    <div class="header-inner">
      <div class="header-left">CREATIVE PRESENTATION</div>
      <div class="header-date">DECEMBER 9, 2025</div>
      <div class="header-arrow">
        <span class="arrow-line"></span>
        <span class="arrow-head">→</span>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
// Không cần logic đặc biệt
</script>

<style scoped lang="scss">
.portfolio-header {
  width: 100vw;
  background: #fff;
  border-bottom: 2px solid var(--color-border);
  box-shadow: 0 2px 12px #7f5fff08;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  z-index: 10;
}
.header-inner {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 2rem 0.5rem 2rem;
  font-family: var(--font-main);
  font-size: 1.05rem;
  font-weight: 600;
  letter-spacing: 0.04em;
}
.header-left {
  color: var(--color-subtext);
}
.header-date {
  color: var(--color-subtext);
}
.header-arrow {
  display: flex;
  align-items: center;
  gap: 0.3em;
}
.arrow-line {
  display: inline-block;
  width: 40px;
  height: 2px;
  background: var(--color-subtext);
  margin-right: 0.2em;
}
.arrow-head {
  font-size: 1.2em;
  color: var(--color-subtext);
}
</style> 