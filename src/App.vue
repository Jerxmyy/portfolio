<script setup>
import { ref, onMounted } from 'vue'
import Header from './components/Header.vue'
import About from './components/About.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

const activeSection = ref('accueil')
const displayedText = ref('')
const isTyping = ref(false)
const isDeleting = ref(false)
const currentPhase = ref(0)

const texts = ['Bonjour, je suis Jérémy', 'Je suis développeur\nfront-end']

const typeWriter = () => {
  if (currentPhase.value >= texts.length) {
    // Redémarrer l'animation en boucle
    currentPhase.value = 0
    setTimeout(() => {
      typeWriter()
    }, 3000)
    return
  }

  const currentText = texts[currentPhase.value]

  if (!isDeleting.value && displayedText.value.length < currentText.length) {
    // Mode écriture
    isTyping.value = true
    isDeleting.value = false
    displayedText.value += currentText.charAt(displayedText.value.length)
    setTimeout(() => typeWriter(), 100)
  } else if (!isDeleting.value && displayedText.value.length === currentText.length) {
    // Fin d'écriture, attendre avant de supprimer
    isTyping.value = false
    setTimeout(() => {
      isDeleting.value = true
      typeWriter()
    }, 2000)
  } else if (isDeleting.value && displayedText.value.length > 0) {
    // Mode suppression
    isTyping.value = true
    displayedText.value = displayedText.value.slice(0, -1)
    setTimeout(() => typeWriter(), 50) // Plus rapide pour la suppression
  } else if (isDeleting.value && displayedText.value.length === 0) {
    // Fin de suppression, passer au texte suivant
    isTyping.value = false
    isDeleting.value = false
    currentPhase.value++
    setTimeout(() => typeWriter(), 500) // Petite pause avant le nouveau texte
  }
}

const scrollToSection = (sectionId) => {
  activeSection.value = sectionId
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  // Démarrer l'effet d'écriture après un court délai
  setTimeout(() => {
    typeWriter()
  }, 1000)

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id
        }
      })
    },
    { threshold: 0.3 },
  )

  const sections = document.querySelectorAll('section[id]')
  sections.forEach((section) => observer.observe(section))
})
</script>

<template>
  <div id="app">
    <Header :active-section="activeSection" @navigate="scrollToSection" />

    <main>
      <section id="accueil" class="hero">
        <div class="hero-content">
          <h1 class="typing-text">
            <span class="dynamic-text"
              >{{ displayedText
              }}<span v-if="isTyping" class="cursor" :class="{ deleting: isDeleting }"
                >|</span
              ></span
            >
          </h1>
          <h2>Développeur Front-end & Creative Developer</h2>
          <p>
            Passionné par le développement web et la création d'expériences digitales innovantes, je
            transforme vos idées en solutions technologiques modernes et performantes.
          </p>
          <div class="hero-buttons">
            <button @click="scrollToSection('projets')" class="btn btn-primary">
              Voir mes projets
            </button>
            <button @click="scrollToSection('contact')" class="btn btn-secondary">
              Me contacter
            </button>
          </div>
        </div>
        <div class="hero-image">
          <div class="code-animation">
            <div class="code-line">
              <span class="keyword">const</span>
              <span class="variable">développeur</span>
              <span class="operator">=</span>
              <span class="string">"Jérémy"</span>
            </div>
            <div class="code-line">
              <span class="keyword">function</span>
              <span class="function">créerProjet</span>
              <span class="bracket">()</span>
              <span class="bracket">{</span>
            </div>
            <div class="code-line indent">
              <span class="keyword">return</span>
              <span class="string">"Excellence"</span>
            </div>
            <div class="code-line">
              <span class="bracket">}</span>
            </div>
          </div>
        </div>
      </section>

      <About />
      <Projects />
      <Contact />
    </main>

    <Footer />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=MedievalSharp&family=Cinzel:wght@400;500;600;700&family=Uncial+Antiqua&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  width: 100%;
  max-width: none;
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}

section {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0;
}

/* Force full width for all sections */
.hero,
.about,
.projects,
.contact {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0;
}

/* Force full width for header and footer */
.header,
.footer {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
  background: linear-gradient(
    135deg,
    #0a0a0a 0%,
    #1a1612 25%,
    #2d1b0f 50%,
    #1a1612 75%,
    #0a0a0a 100%
  );
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  min-height: 100vh;
}

body {
  font-family: 'MedievalSharp', cursive;
  line-height: 1.8;
  color: #c9aa6c;
  background: transparent;
  overflow-x: hidden;
  min-height: 100vh;
  font-size: 16px;
  text-shadow: 0 0 3px rgba(201, 170, 108, 0.3);
}

#app {
  min-height: 100vh;
  width: 100%;
  max-width: none;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

main {
  flex: 1;
}

section {
  padding: 80px 0;
  width: 100%;
  margin: 0;
}

.hero {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
  min-height: 100vh;
  width: 100%;
  max-width: none;
  padding: 120px 40px 80px;
  position: relative;
  overflow: hidden;
  margin: 0;
  box-sizing: border-box;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background:
    radial-gradient(ellipse at top, rgba(212, 175, 55, 0.1) 0%, transparent 70%),
    radial-gradient(ellipse at bottom, rgba(139, 69, 19, 0.08) 0%, transparent 70%);
  pointer-events: none;
}

.hero::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="25" cy="25" r="1" fill="%23d4af37" opacity="0.1"/><circle cx="75" cy="75" r="1" fill="%23d4af37" opacity="0.05"/><circle cx="50" cy="10" r="0.5" fill="%23d4af37" opacity="0.08"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
  opacity: 0.3;
  pointer-events: none;
}

.hero-content {
  position: relative;
  z-index: 2;
}

.hero-content h1 {
  font-size: 3rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: #d4af37;
  text-shadow:
    0 0 10px rgba(212, 175, 55, 0.8),
    0 0 20px rgba(212, 175, 55, 0.6),
    0 0 30px rgba(212, 175, 55, 0.4),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  animation: darkSoulsGlow 4s ease-in-out infinite alternate;
  letter-spacing: 1px;
  line-height: 1.2;
  text-transform: uppercase;
}

.typing-text {
  min-height: 4rem;
  display: flex;
  align-items: center;
}

.dynamic-text {
  display: inline-block;
  min-width: 300px;
  white-space: pre-line;
}

.cursor {
  color: #f4d03f;
  animation: blink 1s infinite;
  font-weight: 300;
  margin-left: 2px;
}

.cursor.deleting {
  color: #e74c3c;
  animation: blink 0.5s infinite;
  font-weight: 400;
}

@keyframes blink {
  0%,
  50% {
    opacity: 1;
  }
  51%,
  100% {
    opacity: 0;
  }
}

.hero-content h2 {
  font-size: 1.6rem;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  color: #c9aa6c;
  margin-bottom: 2rem;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  letter-spacing: 1px;
  line-height: 1.3;
  font-style: italic;
}

.hero-content p {
  font-size: 1.2rem;
  font-family: 'MedievalSharp', cursive;
  color: #b8860b;
  margin-bottom: 3rem;
  line-height: 1.8;
  text-shadow:
    0 0 4px rgba(184, 134, 11, 0.6),
    1px 1px 2px rgba(0, 0, 0, 0.5);
  font-style: italic;
  max-width: 500px;
  letter-spacing: 0.5px;
}

@keyframes darkSoulsGlow {
  from {
    text-shadow:
      0 0 10px rgba(212, 175, 55, 0.8),
      0 0 20px rgba(212, 175, 55, 0.6),
      0 0 30px rgba(212, 175, 55, 0.4),
      2px 2px 4px rgba(0, 0, 0, 0.8);
  }
  to {
    text-shadow:
      0 0 15px rgba(212, 175, 55, 1),
      0 0 30px rgba(212, 175, 55, 0.8),
      0 0 45px rgba(212, 175, 55, 0.6),
      3px 3px 6px rgba(0, 0, 0, 0.9);
  }
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.btn {
  padding: 20px 40px;
  border: 3px solid #8b4513;
  border-radius: 0;
  font-size: 1.1rem;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  cursor: pointer;
  transition: all 0.4s ease;
  text-decoration: none;
  display: inline-block;
  text-align: center;
  position: relative;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.2) 0%, rgba(101, 67, 33, 0.1) 100%);
  color: #d4af37;
  text-shadow:
    0 0 6px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  box-shadow:
    0 6px 20px rgba(139, 69, 19, 0.4),
    inset 0 1px 0 rgba(212, 175, 55, 0.3);
  letter-spacing: 1px;
  overflow: hidden;
  min-width: 180px;
  text-transform: uppercase;
  clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
}

.btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.2), transparent);
  transition: left 0.5s ease;
}

.btn:hover::before {
  left: 100%;
}

.btn:hover {
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.3) 0%, rgba(101, 67, 33, 0.2) 100%);
  color: #f4d03f;
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  box-shadow:
    0 8px 30px rgba(139, 69, 19, 0.6),
    inset 0 1px 0 rgba(212, 175, 55, 0.4);
  transform: translateY(-2px);
  border-color: #d4af37;
}

.btn-primary {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  box-shadow:
    0 6px 20px rgba(139, 69, 19, 0.5),
    inset 0 1px 0 rgba(212, 175, 55, 0.4);
  border-color: #654321;
}

.btn-primary:hover {
  background: linear-gradient(135deg, #a0522d 0%, #8b4513 100%);
  color: #f4d03f;
  text-shadow:
    0 0 12px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  box-shadow:
    0 8px 30px rgba(160, 82, 45, 0.7),
    inset 0 1px 0 rgba(212, 175, 55, 0.5);
}

.btn-secondary {
  background: transparent;
  color: #8b4513;
  border-color: #8b4513;
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  z-index: 2;
}

.code-animation {
  background: linear-gradient(135deg, #0c0c0c 0%, #1a1a1a 50%, #0c0c0c 100%);
  padding: 40px;
  border: 2px solid #d4af37;
  border-radius: 12px;
  font-family: 'Cormorant Garamond', serif;
  font-size: 1rem;
  line-height: 1.8;
  box-shadow:
    0 8px 32px rgba(212, 175, 55, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  animation: float 6s ease-in-out infinite;
  position: relative;
  overflow: hidden;
}

.code-animation::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.1), transparent);
  animation: goldenScan 4s linear infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes goldenScan {
  0% {
    left: -100%;
  }
  100% {
    left: 100%;
  }
}

.code-line {
  margin-bottom: 12px;
  position: relative;
  z-index: 2;
}

.code-line.indent {
  padding-left: 30px;
}

.keyword {
  color: #d4af37;
  text-shadow: 0 0 8px rgba(212, 175, 55, 0.6);
  font-weight: 600;
}
.variable {
  color: #daa520;
  text-shadow: 0 0 6px rgba(218, 165, 32, 0.5);
  font-style: italic;
}
.operator {
  color: #b8860b;
  text-shadow: 0 0 6px rgba(184, 134, 11, 0.5);
}
.string {
  color: #f4d03f;
  text-shadow: 0 0 8px rgba(244, 208, 63, 0.6);
  font-style: italic;
}
.function {
  color: #ffd700;
  text-shadow: 0 0 10px rgba(255, 215, 0, 0.7);
  font-weight: 600;
}
.bracket {
  color: #cd853f;
  text-shadow: 0 0 6px rgba(205, 133, 63, 0.5);
}

@media (max-width: 768px) {
  .hero {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
    padding: 100px 20px 60px;
  }

  .hero-content h1 {
    font-size: 2.5rem;
  }

  .hero-buttons {
    justify-content: center;
  }

  .code-animation {
    font-size: 0.9rem;
    padding: 20px;
  }
}
</style>
