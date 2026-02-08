<template>
  <section id="work" class="work section">
    <div class="container">
      <h2 class="section-title">
        <span class="number">03.</span> Some Things I've Built
      </h2>
      
      <div class="projects">
        <div 
          v-for="(project, index) in projects" 
          :key="index"
          class="project-card"
          :class="{ reverse: index % 2 !== 0 }"
        >
          <div class="project-image">
            <a :href="project.link" target="_blank" rel="noopener noreferrer">
              <div class="image-placeholder">
                 <img :src="project.image" :alt="project.title">
              </div>
            </a>
          </div>
          
          <div class="project-content">
            <p class="project-overline">Featured Project</p>
            <h3 class="project-title">
              <a :href="project.link" target="_blank" rel="noopener noreferrer">
                {{ project.title }}
              </a>
            </h3>
            <div class="project-description">
              <p>{{ project.description }}</p>
            </div>
            <ul class="project-tech">
              <li v-for="tech in project.technologies" :key="tech">{{ tech }}</li>
            </ul>
            <div class="project-links">
              <a v-if="project.github" :href="project.github" target="_blank" rel="noopener noreferrer" aria-label="GitHub">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                </svg>
              </a>
              <a :href="project.link" target="_blank" rel="noopener noreferrer" aria-label="External Link">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                  <polyline points="15 3 21 3 21 9"></polyline>
                  <line x1="10" y1="14" x2="21" y2="3"></line>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    title: 'Chess Engine',
    description: 'I developed a distributed chess engine using Java, combining multithreaded alpha-beta search with a custom RMI-based cluster system. The engine supports parallel game-tree evaluation across multiple machines, integrating move ordering, heuristics, and real-time progress tracking to maximize search efficiency and scalability.',
    technologies: ['Java', 'RMI', 'Multithreading', 'Alpha-Beta Search'],
    github: 'https://github.com/paquimomo/chess-engine',
    link: 'https://github.com/paquimomo/chess-engine',
    image: '/chess-engine.png'
  },
  {
    title: 'Automation framework',
    description: 'Comprehensive test automation framework built with Python and Selenium, featuring 24+ automated tests, Page Object Model architecture, and professional reporting. Demonstrates industry best practices in test automation.',
    technologies: ['Python', 'Selenium', 'Page Object Model', 'Test Reporting'],
    github: 'https://github.com/paquimomo/automation_framework',
    link: 'https://github.com/paquimomo/automation_framework',
    image: '/report.png'
  }
])
</script>

<style scoped>
.work {
  background: var(--surface);
}

.section-title {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 80px;
}

.number {
  color: var(--primary);
  font-size: 24px;
  font-weight: 600;
}

.projects {
  display: flex;
  flex-direction: column;
  gap: 120px;
}

.project-card {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 20px;
  align-items: center;
  position: relative;
}

.project-image {
  grid-column: 1 / 8;
  position: relative;
  z-index: 1;
}

.project-image a {
  display: block;
  position: relative;
  border-radius: 8px;
  overflow: hidden;
}

.image-placeholder {
  background: linear-gradient(135deg, #e0f2fe 0%, #dbeafe 100%);
  aspect-ratio: 16 / 10;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  border: 2px solid var(--border);
}

.image-placeholder p {
  color: var(--primary);
  font-weight: 600;
}

.image-placeholder:hover {
  transform: scale(1.02);
  border-color: var(--primary);
}

.image-placeholder img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(30%);
  transition: filter 0.3s ease;
}

.image-placeholder:hover img {
  filter: grayscale(0%);
}

.project-content {
  grid-column: 7 / -1;
  position: relative;
  z-index: 2;
  text-align: right;
}

.project-card.reverse .project-image {
  grid-column: 6 / -1;
}

.project-card.reverse .project-content {
  grid-column: 1 / 8;
  text-align: left;
}

.project-overline {
  color: var(--primary);
  font-size: 14px;
  font-weight: 500;
  margin-bottom: 8px;
}

.project-title {
  font-size: 28px;
  font-weight: 700;
  margin-bottom: 20px;
}

.project-title a {
  color: var(--text);
  text-decoration: none;
  transition: color 0.3s ease;
}

.project-title a:hover {
  color: var(--primary);
}

.project-description {
  background: var(--surface);
  border-radius: 8px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid var(--border);
}

.project-description p {
  color: var(--text-muted);
  line-height: 1.6;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  list-style: none;
  margin-bottom: 20px;
  justify-content: flex-end;
}

.project-card.reverse .project-tech {
  justify-content: flex-start;
}

.project-tech li {
  font-size: 13px;
  color: var(--text-muted);
  font-family: monospace;
}

.project-links {
  display: flex;
  gap: 16px;
  justify-content: flex-end;
}

.project-card.reverse .project-links {
  justify-content: flex-start;
}

.project-links a {
  color: var(--text-muted);
  transition: all 0.3s ease;
}

.project-links a:hover {
  color: var(--primary);
  transform: translateY(-2px);
}

@media (max-width: 968px) {
  .project-card,
  .project-card.reverse {
    display: flex;
    flex-direction: column;
  }

  .project-image,
  .project-card.reverse .project-image {
    width: 100%;
  }

  .project-content,
  .project-card.reverse .project-content {
    text-align: left;
    width: 100%;
  }

  .project-tech,
  .project-card.reverse .project-tech {
    justify-content: flex-start;
  }

  .project-links,
  .project-card.reverse .project-links {
    justify-content: flex-start;
  }
}
</style>