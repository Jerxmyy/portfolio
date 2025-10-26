<template>
  <header class="header" :class="{ 'header-scrolled': isScrolled }">
    <div class="container">
      <div class="logo">
        <img src="/logo-sans-fond.png" alt="Jérémy" class="logo-img" />
      </div>

      <nav class="nav" :class="{ 'nav-open': isMobileMenuOpen }">
        <ul class="nav-list">
          <li class="nav-item">
            <a
              href="#accueil"
              class="nav-link"
              :class="{ active: activeSection === 'accueil' }"
              @click="handleNavClick('accueil')"
            >
              Accueil
            </a>
          </li>
          <li class="nav-item">
            <a
              href="#apropos"
              class="nav-link"
              :class="{ active: activeSection === 'apropos' }"
              @click="handleNavClick('apropos')"
            >
              À propos
            </a>
          </li>
          <li class="nav-item">
            <a
              href="#projets"
              class="nav-link"
              :class="{ active: activeSection === 'projets' }"
              @click="handleNavClick('projets')"
            >
              Projets
            </a>
          </li>
          <li class="nav-item">
            <a
              href="#contact"
              class="nav-link"
              :class="{ active: activeSection === 'contact' }"
              @click="handleNavClick('contact')"
            >
              Contact
            </a>
          </li>
        </ul>
      </nav>

      <button
        class="mobile-menu-btn"
        @click="toggleMobileMenu"
        :class="{ active: isMobileMenuOpen }"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  activeSection: {
    type: String,
    default: 'accueil',
  },
})

const emit = defineEmits(['navigate'])

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleNavClick = (sectionId) => {
  emit('navigate', sectionId)
  isMobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(12, 12, 12, 0.95);
  backdrop-filter: blur(15px);
  border-bottom: 2px solid #d4af37;
  transition: all 0.4s ease;
  box-shadow: 0 4px 20px rgba(212, 175, 55, 0.2);
}

.header-scrolled {
  background: rgba(12, 12, 12, 0.98);
  box-shadow: 0 6px 30px rgba(212, 175, 55, 0.3);
  border-bottom-color: #f4d03f;
}

.container {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 120px;
  box-sizing: border-box;
}

.logo-img {
  height: 120px;
  width: auto;
  max-width: 360px;
  object-fit: contain;
  filter: drop-shadow(0 0 10px rgba(212, 175, 55, 0.8));
  transition: all 0.4s ease;
  animation: darkSoulsPulse 4s ease-in-out infinite alternate;
}

.logo-img:hover {
  filter: drop-shadow(0 0 15px rgba(212, 175, 55, 1)) drop-shadow(0 0 25px rgba(212, 175, 55, 0.6));
  transform: scale(1.05);
}

@keyframes darkSoulsPulse {
  from {
    text-shadow:
      0 0 10px rgba(212, 175, 55, 0.8),
      2px 2px 4px rgba(0, 0, 0, 0.8);
  }
  to {
    text-shadow:
      0 0 15px rgba(212, 175, 55, 1),
      0 0 25px rgba(212, 175, 55, 0.6),
      3px 3px 6px rgba(0, 0, 0, 0.9);
  }
}

.nav-list {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.nav-link {
  text-decoration: none;
  color: #c9aa6c;
  font-family: 'MedievalSharp', cursive;
  font-size: 1rem;
  font-weight: 400;
  transition: all 0.4s ease;
  position: relative;
  padding: 1rem 1.8rem;
  border: 1px solid transparent;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  letter-spacing: 1px;
  border-radius: 0;
  text-transform: uppercase;
}

.nav-link:hover {
  color: #d4af37;
  text-shadow:
    0 0 10px rgba(212, 175, 55, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  border: 2px solid #8b4513;
  background: rgba(139, 69, 19, 0.2);
  transform: translateY(-2px);
}

.nav-link.active {
  color: #f4d03f;
  text-shadow:
    0 0 12px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  border: 2px solid #d4af37;
  background: rgba(212, 175, 55, 0.2);
}

.nav-link.active::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 50%;
  transform: translateX(-50%);
  width: 60%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #f4d03f, transparent);
  box-shadow: 0 0 10px rgba(244, 208, 63, 0.6);
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  gap: 4px;
}

.mobile-menu-btn span {
  width: 25px;
  height: 3px;
  background: #333;
  transition: all 0.3s ease;
  border-radius: 2px;
}

.mobile-menu-btn.active span:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.mobile-menu-btn.active span:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn.active span:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}

/* Breakpoints responsives */
@media (max-width: 1200px) {
  .container {
    padding: 0 30px;
  }

  .nav-list {
    gap: 1.5rem;
  }

  .nav-link {
    padding: 0.8rem 1.5rem;
    font-size: 0.95rem;
  }
}

@media (max-width: 992px) {
  .container {
    padding: 0 25px;
  }

  .logo-img {
    height: 80px;
    max-width: 300px;
  }

  .nav-list {
    gap: 1rem;
  }

  .nav-link {
    padding: 0.7rem 1.2rem;
    font-size: 0.9rem;
  }
}

@media (max-width: 768px) {
  .container {
    padding: 0 20px;
    height: 80px;
  }

  .logo-img {
    height: 60px;
    max-width: 200px;
  }

  .mobile-menu-btn {
    display: flex;
    z-index: 1001;
  }

  .mobile-menu-btn span {
    background: #d4af37;
    box-shadow: 0 0 6px rgba(212, 175, 55, 0.6);
  }

  .nav {
    position: fixed;
    top: 80px;
    left: 0;
    right: 0;
    background: rgba(12, 12, 12, 0.98);
    backdrop-filter: blur(15px);
    border-bottom: 2px solid #d4af37;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.4s ease;
    z-index: 1000;
    box-shadow: 0 8px 32px rgba(212, 175, 55, 0.3);
  }

  .nav-open {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-list {
    flex-direction: column;
    padding: 2rem 1.5rem;
    gap: 0;
  }

  .nav-link {
    font-size: 1.1rem;
    padding: 1.2rem 0;
    border-bottom: 1px solid rgba(212, 175, 55, 0.2);
    text-align: center;
    width: 100%;
    display: block;
  }

  .nav-link:last-child {
    border-bottom: none;
  }

  .nav-link:hover {
    background: rgba(212, 175, 55, 0.1);
    transform: none;
  }
}

@media (max-width: 480px) {
  .container {
    padding: 0 15px;
    height: 70px;
  }

  .logo-img {
    height: 50px;
    max-width: 150px;
  }

  .nav {
    top: 70px;
  }

  .nav-list {
    padding: 1.5rem 1rem;
  }

  .nav-link {
    font-size: 1rem;
    padding: 1rem 0;
  }
}
</style>
