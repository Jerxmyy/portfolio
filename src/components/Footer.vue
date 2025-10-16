<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <div class="footer-logo">
            <img src="/logo-sans-fond.png" alt="TheCodeOfJeremy" class="footer-logo-img" />
          </div>
          <p>
            Développeur Web passionné, créateur d'expériences digitales modernes et performantes.
          </p>
          <div class="social-links">
            <a
              href="https://github.com/Jerxmyy"
              class="social-link"
              target="_blank"
              aria-label="GitHub"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                />
              </svg>
            </a>
            <a
              href="www.linkedin.com/in/jeremy-chambon-a50aaa29a"
              class="social-link"
              target="_blank"
              aria-label="LinkedIn"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                />
              </svg>
            </a>
            <a href="mailto:jeremy.dev@example.com" class="social-link" aria-label="Email">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"
                />
              </svg>
            </a>
          </div>
        </div>

        <div class="footer-section">
          <h4>Navigation</h4>
          <ul class="footer-links">
            <li><a href="#accueil" @click="scrollToSection('accueil')">Accueil</a></li>
            <li><a href="#apropos" @click="scrollToSection('apropos')">À propos</a></li>
            <li><a href="#projets" @click="scrollToSection('projets')">Projets</a></li>
            <li><a href="#contact" @click="scrollToSection('contact')">Contact</a></li>
          </ul>
        </div>

        <div class="footer-section">
          <h4>Compétences</h4>
          <ul class="footer-links">
            <li>Vue.js & React</li>
            <li>Node.js & Express</li>
            <li>HTML5 & CSS3</li>
            <li>JavaScript ES6+</li>
            <li>MongoDB & MySQL</li>
          </ul>
        </div>

        <div class="footer-section">
          <h4>Contact</h4>
          <div class="contact-info">
            <p>
              <svg
                width="16"
                height="16"
                viewBox="0 0 24 24"
                fill="currentColor"
                style="margin-right: 8px"
              >
                <path
                  d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"
                />
              </svg>
              jeremy.chambon@mail-esd.com
            </p>
            <p>
              <svg
                width="16"
                height="16"
                viewBox="0 0 24 24"
                fill="currentColor"
                style="margin-right: 8px"
              >
                <path
                  d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"
                />
              </svg>
              Paris, France
            </p>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <div class="footer-bottom-content">
          <p>&copy; {{ currentYear }} Jérémy. Tous droits réservés.</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const emit = defineEmits(['navigate'])

const currentYear = computed(() => new Date().getFullYear())

const scrollToSection = (sectionId) => {
  emit('navigate', sectionId)
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #0c0c0c 0%, #1a1a1a 50%, #0c0c0c 100%);
  color: #d4af37;
  padding: 3rem 0 0;
  border-top: 2px solid #d4af37;
  box-shadow: 0 4px 20px rgba(212, 175, 55, 0.2);
}

.container {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0 40px;
  box-sizing: border-box;
}

.footer-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 3rem;
  margin-bottom: 2rem;
}

.footer-logo {
  margin-bottom: 1.5rem;
  display: flex;
  justify-content: flex-start;
}

.footer-logo-img {
  height: 120px;
  width: auto;
  max-width: 200px;
  object-fit: contain;
  filter: drop-shadow(0 0 8px rgba(212, 175, 55, 0.6));
  transition: all 0.4s ease;
}

.footer-logo-img:hover {
  filter: drop-shadow(0 0 12px rgba(212, 175, 55, 0.9));
  transform: scale(1.05);
}

.footer-section h3 {
  font-size: 1.5rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: #f4d03f;
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.6);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.footer-section h4 {
  font-size: 1.2rem;
  font-family: 'Cinzel', serif;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: #e6d7a3;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.5);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.footer-section p {
  color: #e6d7a3;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  font-size: 1rem;
  font-family: 'Cormorant Garamond', serif;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.4);
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.1) 0%, rgba(184, 134, 11, 0.05) 100%);
  color: #d4af37;
  border: 1px solid #d4af37;
  border-radius: 8px;
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 0.8rem;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 500;
  text-shadow: 0 0 8px rgba(212, 175, 55, 0.5);
  box-shadow: 0 2px 8px rgba(212, 175, 55, 0.2);
}

.social-link:hover {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.2) 0%, rgba(184, 134, 11, 0.1) 100%);
  color: #f4d03f;
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.7);
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.4);
  border-color: #f4d03f;
}

.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: 0.5rem;
}

.footer-links a {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: #f4d03f;
  text-shadow: 0 0 8px rgba(244, 208, 63, 0.6);
}

.contact-info p {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
  color: #ccc;
}

.footer-bottom {
  border-top: 1px solid #333;
  padding: 1.5rem 0;
}

.footer-bottom-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-bottom p {
  margin: 0;
  color: #999;
}

.footer-note {
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .footer-logo {
    justify-content: center;
  }

  .footer-logo-img {
    height: 50px;
    max-width: 180px;
  }

  .social-links {
    justify-content: center;
  }

  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
  }

  .footer {
    padding: 2rem 0 0;
  }
}
</style>
