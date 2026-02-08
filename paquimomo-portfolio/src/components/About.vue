<template>
  <section id="about" class="about section">
    <div class="container">
      <h2 class="section-title">
        <span class="number">01.</span> About Me
      </h2>
      <div class="about-content">
        <div class="about-text">
          <p class="intro">
            {{ introText }}
          </p>
          <p class="main-text">
            {{ mainText }}
          </p>
          
          <p class="skills-intro">Here are some technologies I've been working with:</p>
          <ul class="skills-list">
            <li v-for="skill in skills" :key="skill">{{ skill }}</li>
          </ul>
        </div>
        <div class="about-image">
          <div class="image-placeholder">
            <img src="/logo.jpeg" alt="Profile Photo">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const introText = ref('Hello! I\'m Francisco Morales Garcia, a passionate developer based in Guadalajara, Jalisco.')
const mainText = ref('')

const skills = ref([
  'JavaScript',
  'Vue.js',
  'Node.js',
  'Git & GitHub',
  'MongoDB',
  'Java',
  'Python',
  'SQL',
  'Selenium'
])
</script>

<style scoped>
.about {
  background: var(--surface);
}

.section-title {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 48px;
}

.number {
  color: var(--primary);
  font-size: 24px;
  font-weight: 600;
}

.about-content {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: 60px;
  align-items: start;
}

.about-text p {
  margin-bottom: 20px;
  color: var(--text-muted);
  line-height: 1.7;
}

.intro {
  font-size: 18px;
  font-weight: 500;
  color: var(--text);
}

.skills-intro {
  margin-top: 30px;
  font-weight: 500;
  color: var(--text);
}

.skills-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
  margin-top: 16px;
  list-style: none;
}

.skills-list li {
  position: relative;
  padding-left: 24px;
  font-size: 14px;
  color: var(--text-muted);
}

.skills-list li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--primary);
  font-size: 18px;
  line-height: 1;
}

.about-image {
  position: relative;
}

.image-placeholder {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  background: linear-gradient(135deg, #e0f2fe 0%, #dbeafe 100%);
  aspect-ratio: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 3px solid var(--primary);
  transition: all 0.3s ease;
}

.image-placeholder p {
  color: var(--primary);
  font-weight: 600;
  font-size: 18px;
}

.image-placeholder:hover {
  transform: translate(-8px, -8px);
  box-shadow: 8px 8px 0 var(--primary);
}

.image-placeholder img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(20%);
  transition: all 0.3s ease;
}

.image-placeholder:hover img {
  filter: grayscale(0%);
}

@media (max-width: 968px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .image-placeholder {
    max-width: 400px;
    margin: 0 auto;
  }
}

@media (max-width: 480px) {
  .skills-list {
    grid-template-columns: 1fr;
  }
}
</style>