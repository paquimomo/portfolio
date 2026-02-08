<template>
  <nav class="navigation" :class="{ scrolled: isScrolled }">
    <div class="container nav-container">
      <a href="#home" class="logo">
        <div class="logo-inner">{{ logoText }}</div>
      </a>
      
      <div class="nav-links" :class="{ active: mobileMenuOpen }">
        <a 
          v-for="(link, index) in navLinks" 
          :key="link.id"
          :href="link.href"
          class="nav-link"
          :style="{ animationDelay: `${index * 0.1}s` }"
          @click="closeMobileMenu"
        >
          <span class="nav-number">{{ String(index + 1).padStart(2, '0') }}.</span>
          {{ link.text }}
        </a>
      </div>

      <button class="mobile-toggle" @click="toggleMobileMenu" aria-label="Toggle menu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const logoText = 'F'

const navLinks = ref([
  { id: 'about', text: 'About', href: '#about' },
  { id: 'experience', text: 'My Experience', href: '#experience' },
  { id: 'work', text: 'My Work', href: '#work' },
  { id: 'contact', text: 'Contact', href: '#contact' }
])

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
  document.body.style.overflow = mobileMenuOpen.value ? 'hidden' : ''
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
  document.body.style.overflow = ''
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navigation {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 20px 0;
  transition: all 0.3s ease;
  background: transparent;
}

.navigation.scrolled {
  background: rgba(248, 250, 252, 0.9);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.05);
  padding: 12px 0;
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  width: 50px;
  height: 50px;
  border: 2px solid var(--primary);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  background: var(--surface);
  text-decoration: none;
  transition: all 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(59, 130, 246, 0.2);
}

.logo-inner {
  color: var(--primary);
  font-weight: 700;
  font-size: 24px;
}

.nav-links {
  display: flex;
  gap: 40px;
  align-items: center;
}

.nav-link {
  color: var(--text-muted);
  text-decoration: none;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  display: flex;
  align-items: center;
  gap: 6px;
}

.nav-number {
  color: var(--primary);
  font-size: 12px;
  font-weight: 600;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary);
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: var(--text);
}

.nav-link:hover::after {
  width: 100%;
}

.mobile-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
}

.mobile-toggle span {
  width: 25px;
  height: 2px;
  background: var(--text);
  transition: all 0.3s ease;
}

@media (max-width: 768px) {
  .mobile-toggle {
    display: flex;
  }

  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    height: 100vh;
    background: var(--surface);
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 40px;
    box-shadow: -5px 0 20px rgba(0, 0, 0, 0.1);
    transition: right 0.4s ease;
    gap: 30px;
  }

  .nav-links.active {
    right: 0;
  }

  .nav-link {
    font-size: 18px;
    opacity: 0;
    animation: slideInRight 0.4s ease forwards;
  }

  .mobile-toggle.active span:nth-child(1) {
    transform: rotate(45deg) translate(6px, 6px);
  }

  .mobile-toggle.active span:nth-child(2) {
    opacity: 0;
  }

  .mobile-toggle.active span:nth-child(3) {
    transform: rotate(-45deg) translate(6px, -6px);
  }
}

@keyframes slideInRight {
  to {
    opacity: 1;
  }
}
</style>