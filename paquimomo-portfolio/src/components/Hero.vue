<template>
  <section id="home" class="hero">
    <div class="container">
      <div class="hero-content">
        <p class="greeting fade-in-up">Hi, my name is</p>
        <h1 class="name fade-in-up" style="animation-delay: 0.1s">{{ name }}</h1>
        <h2 class="tagline fade-in-up" style="animation-delay: 0.2s">{{ tagline }}</h2>
        <p class="description fade-in-up" style="animation-delay: 0.3s">
          {{ description }}
          <span class="highlight">{{ descriptionHighlight }}</span>
        </p>
        <a :href="ctaLink" class="cta fade-in-up" style="animation-delay: 0.4s">
          {{ ctaText }}
        </a>
      </div>
    </div>
    <div class="decorative-element"></div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('Francisco Morales Garcia.')
const tagline = ref('Software Developer.')
const description = ref("Engineering student with strong foundations in software development, software testing, Python scripting and Linux environments. Experience designing and executing automated test cases for web and system applications. Skilled in debugging, Git-based workflows and continuous integration pipelines.")
const descriptionHighlight = ref('Seeking to contribute as a QA Automation in enterprise-level software products.')
const ctaText = ref('Contact Me')
const ctaLink = ref('#contact')
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 100px 20px 40px;
  position: relative;
  background: linear-gradient(135deg, #f8fafc 0%, #e0f2fe 100%);
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -30%;
  right: -10%;
  width: 60%;
  height: 120%;
  background: radial-gradient(circle, rgba(59, 130, 246, 0.08) 0%, transparent 70%);
  pointer-events: none;
}

.hero::after {
  content: '';
  position: absolute;
  bottom: -20%;
  left: -10%;
  width: 50%;
  height: 80%;
  background: radial-gradient(circle, rgba(14, 165, 233, 0.06) 0%, transparent 70%);
  pointer-events: none;
}

.hero-content {
  max-width: 900px;
  position: relative;
  z-index: 1;
}

.greeting {
  font-size: 16px;
  color: var(--text-muted);
  margin-bottom: 16px;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.name {
  font-size: clamp(48px, 8vw, 84px);
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 16px;
  color: var(--text);
}

.tagline {
  font-size: clamp(32px, 5vw, 56px);
  font-weight: 400;
  line-height: 1.3;
  margin-bottom: 32px;
  color: var(--text);
}

.description {
  max-width: 600px;
  font-size: 17px;
  line-height: 1.7;
  color: var(--text-muted);
  margin-bottom: 48px;
}

.highlight {
  color: var(--primary);
  font-weight: 600;
}

.cta {
  display: inline-flex;
  padding: 16px 36px;
  background: transparent;
  color: var(--text);
  text-decoration: none;
  border: 2px solid var(--primary);
  border-radius: 6px;
  font-weight: 600;
  font-size: 15px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.cta::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  transition: left 0.4s ease;
  z-index: -1;
}

.cta:hover::before {
  left: 0;
}

.cta:hover {
  color: #fff;
  border-color: var(--secondary);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(59, 130, 246, 0.25);
}

.decorative-element {
  position: absolute;
  width: 400px;
  height: 400px;
  border-radius: 50%;
  background: var(--primary);
  filter: blur(80px);
  opacity: 0.15;
  top: 30%;
  right: 5%;
  animation: float 20s ease-in-out infinite;
  pointer-events: none;
}

@keyframes float {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  33% {
    transform: translate(30px, -30px) scale(1.1);
  }
  66% {
    transform: translate(-20px, 20px) scale(0.9);
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 120px 20px 60px;
  }
}
</style>