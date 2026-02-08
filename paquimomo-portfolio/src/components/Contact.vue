<template>
  <section id="contact" class="contact section">
    <div class="container">
      <div class="contact-content">
        <p class="overline">
          <span class="number">04.</span> What's Next?
        </p>
        <h2 class="title">Get In Touch</h2>
        <p class="description">
          {{ contactText }}
        </p>
        <a :href="`mailto:${email}`" class="contact-button">Say Hello</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const contactText = ref("I'm currently looking for new opportunities, my inbox is always open. Whether you have a question or just want to say hi, I'll try my best to get back to you!")
const email = ref('pacofut.moralesg@gmail.com')
</script>

<style scoped>
.contact {
  background: var(--background);
  min-height: 80vh;
  display: flex;
  align-items: center;
}

.contact-content {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.overline {
  color: var(--primary);
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.number {
  font-weight: 600;
}

.title {
  font-size: clamp(40px, 5vw, 60px);
  font-weight: 700;
  color: var(--text);
  margin-bottom: 24px;
}

.description {
  color: var(--text-muted);
  line-height: 1.7;
  margin-bottom: 48px;
}

.contact-button {
  display: inline-block;
  padding: 18px 40px;
  background: transparent;
  color: var(--primary);
  text-decoration: none;
  border: 2px solid var(--primary);
  border-radius: 6px;
  font-weight: 600;
  font-size: 16px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.contact-button::before {
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

.contact-button:hover::before {
  left: 0;
}

.contact-button:hover {
  color: #fff;
  border-color: var(--secondary);
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(59, 130, 246, 0.25);
}
</style>