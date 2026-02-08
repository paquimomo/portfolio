<template>
  <div class="home">
    <Hero />
    <About />
    <Experience />
    <Work />
    <Contact />
    <Footer />
  </div>
</template>

<script setup>
import Hero from '../components/Hero.vue'
import About from '../components/About.vue'
import Experience from '../components/Experience.vue'
import Work from '../components/Work.vue'
import Contact from '../components/Contact.vue'
import Footer from '../components/Footer.vue'
</script>

<style scoped>
.home {
  width: 100%;
}
</style>