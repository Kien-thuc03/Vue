<template>
  <div class="portfolio-wrapper">
    <Header />
    <div class="portfolio-content">
      <!-- Hero Section -->
      <section class="portfolio-hero">
        <div class="hero-bg-blur"></div>
        <div class="hero-content">
          <div class="hero-icons" ref="iconRef">
            <span class="icon-star">✦</span>
          </div>
          <h1 class="hero-title" ref="titleRef">PORTFOLIO</h1>
          <div class="hero-sub" ref="subRef">NGUYỄN KIẾN THỨC</div>
        </div>
        <div class="hero-art"></div>
      </section>
      <!-- Projects Timeline Section -->
      <section class="projects-timeline-section">
        <h2 class="projects-title">DỰ ÁN NỔI BẬT</h2>
        <div class="timeline-pro">
          <div v-for="(project, i) in projects" :key="project.title" class="timeline-pro-item" :ref="el => projectRefs[i] = el">
            <div class="timeline-pro-dot-wrap">
              <div class="timeline-pro-dot">{{ i + 1 }}</div>
              <div class="timeline-pro-line" v-if="i < projects.length - 1"></div>
            </div>
            <div class="timeline-pro-content">
              <div class="timeline-pro-card">
                <div class="timeline-pro-img-wrap">
                  <img :src="project.img" :alt="project.title" />
                </div>
                <div class="timeline-pro-info">
                  <h3>{{ project.title }}</h3>
                  <div class="project-tags">
                    <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
                  </div>
                  <p>{{ project.desc }}</p>
                  <div class="timeline-links">
                    <a v-if="project.demo" :href="project.demo" target="_blank" class="btn-pro demo">Demo</a>
                    <a v-if="project.github" :href="project.github" target="_blank" class="btn-pro github">GitHub</a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import * as anime from 'animejs'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

const titleRef = ref<HTMLElement | null>(null)
const subRef = ref<HTMLElement | null>(null)
const iconRef = ref<HTMLElement | null>(null)
const projectRefs = ref<any[]>([])

const projects = [
  {
    title: 'Landing Page Sản phẩm',
    desc: 'Thiết kế và code landing page chuyển đổi cao, hiệu ứng động mượt mà, responsive.',
    img: 'https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80',
    demo: 'https://your-landingpage-demo.com',
    github: 'https://github.com/your-github/landing-page',
    tags: ['Vue', 'GSAP', 'UI/UX']
  },
  {
    title: 'Dashboard Quản trị',
    desc: 'Xây dựng dashboard realtime với Vue3, Pinia, Chart.js, tối ưu UX cho admin.',
    img: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?auto=format&fit=crop&w=600&q=80',
    demo: '',
    github: 'https://github.com/your-github/dashboard-vue',
    tags: ['Vue', 'Pinia', 'Chart.js']
  },
  {
    title: 'Portfolio Animation',
    desc: 'Portfolio cá nhân với hiệu ứng động Anime.js, tối ưu SEO, điểm Lighthouse cao.',
    img: 'https://images.unsplash.com/photo-1519125323398-675f0ddb6308?auto=format&fit=crop&w=600&q=80',
    demo: 'https://your-portfolio-demo.com',
    github: '',
    tags: ['Vue', 'Anime.js', 'SEO']
  }
]

onMounted(() => {
  (anime as any).default.timeline({})
    .add({
      targets: iconRef.value?.children,
      translateY: [-30, 0],
      opacity: [0, 1],
      delay: (anime as any).default.stagger(120),
      easing: 'easeOutBack',
      duration: 600
    })
    .add({
      targets: titleRef.value,
      translateY: [-60, 0],
      opacity: [0, 1],
      easing: 'easeOutExpo',
      duration: 900
    }, '-=300')
    .add({
      targets: subRef.value,
      translateY: [-20, 0],
      opacity: [0, 1],
      easing: 'easeOutExpo',
      duration: 600
    }, '-=500')
    .add({
      targets: projectRefs.value.filter(el => el instanceof HTMLElement),
      translateY: [60, 0],
      opacity: [0, 1],
      delay: (anime as any).default.stagger(180),
      easing: 'easeOutExpo',
      duration: 700
    }, '-=200')
})
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@700;900&display=swap');

.portfolio-wrapper {
  width: 100vw;
  min-height: 100vh;
  background: var(--color-bg);
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
  align-items: stretch;
}

.portfolio-content {
  max-width: 100%;
  margin: 32px auto 32px auto;
  border-radius: 24px;
  box-shadow: 0 4px 32px #7f5fff11;
  background: var(--color-bg);
  flex: 1;
  width: 100%;
  display: flex;
  flex-direction: column;
  padding: 0 32px;
}

.portfolio-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.2rem 2rem 0.5rem 2rem;
  border-top-left-radius: 18px;
  border-top-right-radius: 18px;
  border-bottom: 2px solid var(--color-border);
  background: #fff;
  font-family: var(--font-main);
  font-size: 1.05rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  position: relative;
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

.portfolio-hero {
  position: relative;
  padding: 2.5rem 0 2.5rem 0;
  background: #fff;
  border-bottom: 2px solid var(--color-border);
  overflow: hidden;
  min-height: 320px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero-bg-blur {
  position: absolute;
  right: -80px;
  top: 10px;
  width: 380px;
  height: 220px;
  background: radial-gradient(circle at 60% 40%, #7f5fff55 60%, #00e0ff33 100%);
  filter: blur(32px);
  z-index: 0;
}
.hero-content {
  position: relative;
  z-index: 2;
  text-align: left;
  max-width: 600px;
}
.hero-icons {
  display: flex;
  flex-direction: column;
  gap: 0.2em;
  font-size: 1.5em;
  color: var(--color-primary);
  margin-bottom: 0.5em;
}
.hero-title {
  font-size: 4.2rem;
  font-weight: 900;
  line-height: 1.05;
  color: var(--color-primary);
  letter-spacing: 0.01em;
  margin-bottom: 0.2em;
  text-shadow: 0 4px 32px #7f5fff33;
}
.hero-sub {
  font-size: 1.1rem;
  color: var(--color-subtext);
  font-weight: 600;
  margin-bottom: 0.5em;
  letter-spacing: 0.04em;
}
.hero-art {
  position: absolute;
  right: 0;
  bottom: -30px;
  width: 320px;
  height: 160px;
  background: radial-gradient(circle at 60% 40%, #7f5fff88 60%, #00e0ff33 100%);
  filter: blur(24px);
  z-index: 1;
}

.projects-timeline-section {
  background: var(--color-bg);
  padding: 2.5rem 0 2.5rem 0;
}
.timeline-pro {
  position: relative;
  margin: 0 auto;
  max-width: 900px;
  padding: 2rem 0 2rem 0;
  display: flex;
  flex-direction: column;
  gap: 0;
}
.timeline-pro-item {
  display: flex;
  align-items: flex-start;
  position: relative;
  min-height: 180px;
  margin-bottom: 0;
}
.timeline-pro-dot-wrap {
  position: relative;
  width: 70px;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 2;
}
.timeline-pro-dot {
  width: 38px;
  height: 38px;
  background: var(--color-accent);
  color: #fff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 800;
  font-size: 1.2rem;
  box-shadow: 0 2px 8px #00e0ff33;
  margin-top: 0;
  margin-bottom: 0;
  z-index: 2;
}
.timeline-pro-line {
  width: 4px;
  height: calc(100% - 38px);
  background: linear-gradient(to bottom, var(--color-accent), #e0eafc);
  margin-top: 0;
  border-radius: 2px;
  z-index: 1;
}
.timeline-pro-content {
  flex: 1;
  padding-left: 0;
  display: flex;
  align-items: flex-start;
}
.timeline-pro-card {
  display: flex;
  align-items: flex-start;
  background: #181c2f;
  color: #fff;
  border-radius: 18px;
  box-shadow: 0 4px 32px #7f5fff22;
  padding: 1.5rem 2rem;
  margin-bottom: 2.5rem;
  min-height: 160px;
  width: 100%;
  gap: 2rem;
  transition: box-shadow 0.2s, transform 0.2s;
  border: 1px solid var(--color-border);
  &:hover {
    box-shadow: 0 8px 32px #00e0ff55;
    transform: translateY(-6px) scale(1.03);
  }
}
.timeline-pro-img-wrap {
  width: 120px;
  min-width: 120px;
  height: 120px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 12px #7f5fff11;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
.timeline-pro-img-wrap img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 12px;
}
.timeline-pro-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.5em;
}
.timeline-pro-info h3 {
  font-size: 1.15rem;
  font-weight: 800;
  color: var(--color-primary);
  margin: 0 0 0.2em 0;
}
.project-tags {
  margin-bottom: 0.3em;
}
.project-tags span {
  display: inline-block;
  background: var(--color-accent);
  color: #fff;
  font-size: 0.92em;
  font-weight: 600;
  border-radius: 12px;
  padding: 0.25em 0.9em;
  margin-right: 0.6em;
  margin-bottom: 0.3em;
  letter-spacing: 0.03em;
}
.timeline-pro-info p {
  color: #e0eafc;
  font-size: 1.05rem;
  margin-bottom: 0.5em;
}
.timeline-links {
  margin-bottom: 0.5em;
}
.btn-pro {
  display: inline-block;
  font-weight: 700;
  font-size: 1em;
  border-radius: 999px;
  padding: 0.5em 1.5em;
  margin-right: 1em;
  background: var(--color-gradient);
  color: #fff;
  text-decoration: none;
  box-shadow: 0 2px 8px #7f5fff22;
  transition: background 0.18s, color 0.18s, transform 0.18s;
}
.btn-pro.github {
  background: #fff;
  color: #181c2f;
}
.btn-pro.demo:hover {
  background: var(--color-primary);
}
.btn-pro.github:hover {
  background: var(--color-accent);
  color: #fff;
}
@media (max-width: 900px) {
  .timeline-pro {
    max-width: 98vw;
    padding: 0;
  }
  .timeline-pro-card {
    flex-direction: column;
    align-items: flex-start;
    padding: 1.2rem 1rem;
    gap: 1rem;
  }
  .timeline-pro-img-wrap {
    width: 100%;
    min-width: 0;
    height: 180px;
    margin-bottom: 1rem;
  }
}

.portfolio-footer {
  background: #fff;
  border-top: 2px solid var(--color-border);
  padding: 1.2rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5em;
  font-size: 1.05rem;
  color: var(--color-subtext);
  border-bottom-left-radius: 18px;
  border-bottom-right-radius: 18px;
}
.footer-socials {
  display: flex;
  gap: 1.2em;
  margin-bottom: 0.2em;
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

@media (max-width: 900px) {
  .portfolio-header, .portfolio-footer {
    padding-left: 1rem;
    padding-right: 1rem;
  }
}
@media (max-width: 600px) {
  .portfolio-hero {
    padding: 1.2rem 0.5rem 1.2rem 0.5rem;
  }
  .hero-title {
    font-size: 2.2rem;
  }
  .projects-timeline-section {
    padding: 1.2rem 0.5rem 1.2rem 0.5rem;
  }
}
</style> 