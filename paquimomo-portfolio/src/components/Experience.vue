<template>
  <section id="experience" class="experience section">
    <div class="container">
      <h2 class="section-title">
        <span class="number">02.</span> Where I've Worked
      </h2>
      
      <div class="experience-container">
        <div class="company-tabs">
          <button 
            v-for="(job, index) in jobs" 
            :key="index"
            @click="activeJob = index"
            :class="{ active: activeJob === index }"
            class="company-tab"
          >
            {{ job.company }}
          </button>
        </div>
        
        <div class="job-details">
          <h3 class="job-title">
            {{ jobs[activeJob].title }}
            <span class="company-name">@ {{ jobs[activeJob].company }}</span>
          </h3>
          <p class="job-duration">{{ jobs[activeJob].duration }}</p>
          
          <ul class="job-responsibilities">
            <li v-for="(task, index) in jobs[activeJob].responsibilities" :key="index">
              {{ task }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeJob = ref(0)

const jobs = ref([
  {
    company: 'Freelance',
    title: 'QA Engineer',
    duration: 'March 2024 - Present',
    responsibilities: [
      'Designed and executed comprehensive test cases for web applications, ensuring high-quality releases and improved user experience.',
      'Collaborated with developers to reproduce issues and verify fixes, contributing to a more efficient development process.',
      'Utilized Selenium WebDriver to automate regression testing, reducing manual testing time by 30% and increasing test coverage.',
    ]
  }
])
</script>

<style scoped>
.experience {
  background: var(--background);
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

.experience-container {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 40px;
  max-width: 900px;
}

.company-tabs {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.company-tab {
  background: transparent;
  border: none;
  border-left: 2px solid var(--border);
  padding: 12px 20px;
  text-align: left;
  font-size: 14px;
  font-weight: 500;
  color: var(--text-muted);
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: 'DM Sans', sans-serif;
}

.company-tab:hover {
  background: rgba(59, 130, 246, 0.05);
  color: var(--primary);
}

.company-tab.active {
  color: var(--primary);
  border-left-color: var(--primary);
  background: rgba(59, 130, 246, 0.05);
}

.job-details {
  animation: fadeIn 0.4s ease;
}

.job-title {
  font-size: 24px;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 4px;
}

.company-name {
  color: var(--primary);
}

.job-duration {
  font-size: 14px;
  color: var(--text-muted);
  margin-bottom: 24px;
  font-family: monospace;
}

.job-responsibilities {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.job-responsibilities li {
  position: relative;
  padding-left: 28px;
  color: var(--text-muted);
  line-height: 1.6;
}

.job-responsibilities li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--primary);
  font-size: 20px;
  line-height: 1;
}

@media (max-width: 768px) {
  .experience-container {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .company-tabs {
    flex-direction: row;
    overflow-x: auto;
  }

  .company-tab {
    border-left: none;
    border-bottom: 2px solid var(--border);
    white-space: nowrap;
  }

  .company-tab.active {
    border-left: none;
    border-bottom-color: var(--primary);
  }
}
</style>