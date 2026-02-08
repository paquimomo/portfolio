<template>
  <footer class="footer">
    <div class="container">
      <div class="social-links">
        <a 
          v-for="social in socialLinks" 
          :key="social.name"
          :href="social.url" 
          target="_blank" 
          rel="noopener noreferrer"
          :aria-label="social.name"
        >
          <component :is="social.icon" />
        </a>
      </div>
      <p class="credit">
        Built by <span>{{ yourName }}</span>
      </p>
    </div>
  </footer>
</template>

<script setup>
import { ref, h } from 'vue'

// CUSTOMIZE THIS: Add your name and social links
const yourName = ref('Francisco Morales')

const socialLinks = ref([
  {
    name: 'GitHub',
    url: 'https://github.com/paquimomo',
    icon: () => h('svg', { width: 20, height: 20, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
      h('path', { d: 'M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22' })
    ])
  },
  {
    name: 'LinkedIn',
    url: 'https://www.linkedin.com/in/franciscomorgar',
    icon: () => h('svg', { width: 20, height: 20, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
      h('path', { d: 'M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z' }),
      h('rect', { x: 2, y: 9, width: 4, height: 12 }),
      h('circle', { cx: 4, cy: 4, r: 2 })
    ])
  }
])
</script>

<style scoped>
.footer {
  padding: 40px 0;
  background: var(--surface);
  border-top: 1px solid var(--border);
}

.footer .container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.social-links {
  display: flex;
  gap: 24px;
}

.social-links a {
  color: var(--text-muted);
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.social-links a:hover {
  color: var(--primary);
  transform: translateY(-3px);
}

.credit {
  font-size: 14px;
  color: var(--text-muted);
}

.credit span {
  color: var(--primary);
  font-weight: 600;
}
</style>