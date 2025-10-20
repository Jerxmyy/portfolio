<template>
  <section id="projets" class="projects">
    <div class="container">
      <div class="section-header">
        <h2>Mes Projets</h2>
        <p>Découvrez quelques-unes de mes réalisations récentes</p>
      </div>

      <div class="projects-filter">
        <button
          v-for="category in categories"
          :key="category"
          @click="activeCategory = category"
          :class="['filter-btn', { active: activeCategory === category }]"
        >
          {{ category }}
        </button>
      </div>

      <div class="projects-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="project-card"
          @click="openProjectModal(project)"
        >
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
            <div class="project-overlay">
              <h4 class="overlay-title">{{ project.title }}</h4>
              <div class="project-links">
                <a :href="project.demo" target="_blank" class="project-link" v-if="project.demo">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path
                      d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"
                    />
                  </svg>
                  Voir le projet
                </a>

                <!-- Layout spécial pour Musée Explorer -->
                <div
                  v-if="project.id === 4 && (project.github || project.githubBackend)"
                  class="project-links-row"
                >
                  <a
                    :href="project.github"
                    target="_blank"
                    class="project-link project-link-small"
                    v-if="project.github"
                  >
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
                      <path
                        d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                      />
                    </svg>
                    Frontend
                  </a>
                  <a
                    :href="project.githubBackend"
                    target="_blank"
                    class="project-link project-link-small"
                    v-if="project.githubBackend"
                  >
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
                      <path
                        d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                      />
                    </svg>
                    Backend
                  </a>
                </div>

                <!-- Layout normal pour les autres projets -->
                <a
                  :href="project.github"
                  target="_blank"
                  class="project-link"
                  v-if="project.github && project.id !== 4"
                >
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path
                      d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                    />
                  </svg>
                  Code source
                </a>
              </div>
            </div>
          </div>

          <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>

            <div class="project-tech">
              <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal pour afficher les détails du projet -->
    <div v-if="selectedProject" class="modal-overlay" @click="closeProjectModal">
      <div class="modal-content" @click.stop>
        <button class="modal-close" @click="closeProjectModal">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
            <path
              d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"
            />
          </svg>
        </button>

        <div class="modal-image">
          <img :src="selectedProject.image" :alt="selectedProject.title" />
        </div>

        <div class="modal-body">
          <h2>{{ selectedProject.title }}</h2>
          <p class="modal-description">{{ selectedProject.description }}</p>

          <div class="modal-details">
            <div class="modal-section">
              <h4>Technologies utilisées</h4>
              <div class="tech-tags">
                <span v-for="tech in selectedProject.technologies" :key="tech" class="tech-tag">
                  {{ tech }}
                </span>
              </div>
            </div>

            <div class="modal-section" v-if="selectedProject.features">
              <h4>Fonctionnalités</h4>
              <ul class="features-list">
                <li v-for="feature in selectedProject.features" :key="feature">
                  {{ feature }}
                </li>
              </ul>
            </div>
          </div>

          <div class="modal-actions">
            <a
              v-if="selectedProject.demo"
              :href="selectedProject.demo"
              target="_blank"
              class="btn btn-primary"
            >
              Voir le projet
            </a>
            <a
              v-if="selectedProject.github"
              :href="selectedProject.github"
              target="_blank"
              class="btn btn-secondary"
            >
              {{ selectedProject.githubBackend ? 'Frontend' : 'Code source' }}
            </a>
            <a
              v-if="selectedProject.githubBackend"
              :href="selectedProject.githubBackend"
              target="_blank"
              class="btn btn-secondary"
            >
              Backend
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('Tous')
const selectedProject = ref(null)

const categories = ['Tous', 'Frontend', 'Full-stack', 'Backend']

const projects = [
  {
    id: 1,
    title: 'Hub Gaming Pop Corn 2024',
    description: "Hub des jeux Pop Corn réalisé dans le cadre du Digital Event 2024 à l'ESD Paris",
    image: 'image-projet/hub-gaming-pop-corn-2024.png',
    category: 'Frontend',
    technologies: ['HTML5', 'CSS3', 'JavaScript'],
    demo: 'https://jchambon.esd-monsite.fr/hub-gaming-pop-corn-2024',
  },
  {
    id: 2,
    title: 'Food Truck Holly Thai',
    description:
      "Site factice pour un food truck thaïlandais dans le cadre d'un projet étudiant réalisé a l'ESD Paris",
    image: 'image-projet/logo-holly-thai.jpg',
    category: 'Backend',
    technologies: ['PHP', 'HTML5', 'CSS3'],
    demo: 'https://jchambon.esd-monsite.fr/restau_thai/',
  },
  {
    id: 3,
    title: 'PixelBay',
    description:
      "Site factice d'achats de jeux vidéos dématérialisés réalisé dans le cadre d'un projet étudiant à l'ESD Paris, inspiré du Site Instant Gaming",
    image: 'image-projet/illustration-pixelbay.jpg',
    category: 'Full-stack',
    technologies: ['JavaScript', 'CSS3', 'HTML5', 'Supabase'],
    demo: 'https://projet-fullstack-eta.vercel.app/',
    github: 'https://github.com/Jerxmyy/projet-fullstack',
    features: [
      'Filtrage par plateforme',
      "Pop up d'ajout au panier",
      "Pop up d'ajout à la wishlist",
      'Indication du genre',
      "Indication de l'éditeur",
      'Indication du studio de développement',
      'Description du jeu',
      'Gestion de la différence de prix entre différentes éditions du jeu',
      'Design responsive',
    ],
  },
  {
    id: 4,
    title: 'Musée Explorer',
    description: "Workshop API utilisant l'API Open Data du Ministère de la culture",
    image: 'image-projet/logo-musee-explorer.png',
    category: 'Full-stack',
    technologies: ['Vue.js', 'Node.js', 'Python', 'Supabase'],
    demo: 'https://workshop-musee.vercel.app',
    github: 'https://github.com/Jerxmyy/workshop_musee',
    githubBackend: 'https://github.com/Jerxmyy/workshop_musee_backend',
    features: [
      'Découverte des musées français',
      'Recherche avancée par critères',
      'Système de filtrage dynamique',
      'Interface responsive et moderne',
      'Exploration interactive des collections',
      'Géolocalisation des musées',
      'Informations détaillées sur chaque musée',
      'Interface utilisateur intuitive',
    ],
  },
]

const filteredProjects = computed(() => {
  if (activeCategory.value === 'Tous') {
    return projects
  }
  return projects.filter((project) => project.category === activeCategory.value)
})

const openProjectModal = (project) => {
  selectedProject.value = project
  document.body.style.overflow = 'hidden'
}

const closeProjectModal = () => {
  selectedProject.value = null
  document.body.style.overflow = 'auto'
}
</script>

<style scoped>
.projects {
  padding: 100px 40px;
  position: relative;
  overflow: hidden;
  width: 100%;
  max-width: none;
  margin: 0;
  box-sizing: border-box;
}

.projects::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background:
    radial-gradient(ellipse at top, rgba(212, 175, 55, 0.08) 0%, transparent 70%),
    radial-gradient(ellipse at bottom, rgba(139, 69, 19, 0.06) 0%, transparent 70%);
  pointer-events: none;
}

.container {
  width: 100%;
  max-width: none;
  margin: 0;
  padding: 0 40px;
  position: relative;
  z-index: 2;
  box-sizing: border-box;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-header h2 {
  font-size: 2.5rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #d4af37;
  text-shadow:
    0 0 10px rgba(212, 175, 55, 0.8),
    0 0 20px rgba(212, 175, 55, 0.6),
    0 0 30px rgba(212, 175, 55, 0.4),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  margin-bottom: 1.5rem;
  animation: darkSoulsGlow 4s ease-in-out infinite alternate;
  letter-spacing: 1px;
  line-height: 1.2;
  text-transform: uppercase;
}

.section-header p {
  font-size: 1.3rem;
  color: #c9aa6c;
  max-width: 700px;
  margin: 0 auto;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  font-family: 'MedievalSharp', cursive;
  font-style: italic;
  line-height: 1.6;
  letter-spacing: 0.5px;
}

.projects-filter {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 1rem 2rem;
  border: 2px solid #8b4513;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.2) 0%, rgba(101, 67, 33, 0.1) 100%);
  border-radius: 0;
  cursor: pointer;
  transition: all 0.4s ease;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  font-size: 1rem;
  color: #c9aa6c;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  letter-spacing: 1px;
  text-transform: uppercase;
}

.filter-btn:hover {
  border-color: #d4af37;
  color: #d4af37;
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.2) 0%, rgba(184, 134, 11, 0.1) 100%);
  text-shadow:
    0 0 10px rgba(212, 175, 55, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  transform: translateY(-2px);
}

.filter-btn.active {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #d4af37;
  border-color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2rem;
}

.project-card {
  background: linear-gradient(135deg, rgba(12, 12, 12, 0.9) 0%, rgba(26, 26, 26, 0.8) 100%);
  border: 2px solid #d4af37;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(212, 175, 55, 0.2);
  transition: all 0.4s ease;
  cursor: pointer;
  position: relative;
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 40px rgba(212, 175, 55, 0.4);
  border-color: #f4d03f;
}

.project-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.98) 0%, rgba(101, 67, 33, 0.95) 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
  padding: 2rem 1.5rem;
  text-align: center;
  backdrop-filter: blur(3px);
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.overlay-title {
  font-size: 1.4rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #d4af37;
  text-shadow:
    0 0 15px rgba(212, 175, 55, 1),
    0 0 25px rgba(212, 175, 55, 0.8),
    2px 2px 4px rgba(0, 0, 0, 0.9);
  margin-bottom: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  line-height: 1.2;
  z-index: 10;
  position: relative;
}

.project-links {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  width: 100%;
  max-width: 280px;
}

.project-links-row {
  display: flex;
  gap: 0.6rem;
  justify-content: center;
  width: 100%;
}

.project-link {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.8rem 1.2rem;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.4) 0%, rgba(101, 67, 33, 0.3) 100%);
  color: #d4af37;
  text-decoration: none;
  border-radius: 0;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  font-size: 0.85rem;
  transition: all 0.3s ease;
  border: 2px solid #8b4513;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 3px rgba(0, 0, 0, 0.8);
  width: 100%;
  backdrop-filter: blur(5px);
}

.project-link-small {
  padding: 0.6rem 1rem;
  font-size: 0.75rem;
  min-width: 80px;
  flex: 1;
  max-width: 120px;
}

.project-link:hover {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #f4d03f;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  border-color: #d4af37;
}

.project-content {
  padding: 1.5rem;
}

.project-content h3 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  letter-spacing: 0.5px;
  line-height: 1.3;
  text-transform: uppercase;
}

.project-content p {
  color: #c9aa6c;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  font-size: 1.1rem;
  font-family: 'MedievalSharp', cursive;
  text-shadow:
    0 0 4px rgba(201, 170, 108, 0.6),
    1px 1px 2px rgba(0, 0, 0, 0.5);
  font-style: italic;
  letter-spacing: 0.5px;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.2) 0%, rgba(101, 67, 33, 0.1) 100%);
  color: #d4af37;
  padding: 0.6rem 1rem;
  border: 2px solid #8b4513;
  border-radius: 0;
  font-size: 0.9rem;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  text-shadow:
    0 0 6px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.tech-tag:hover {
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.3) 0%, rgba(101, 67, 33, 0.2) 100%);
  color: #f4d03f;
  border-color: #d4af37;
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 2rem;
}

.modal-content {
  background: linear-gradient(135deg, rgba(12, 12, 12, 0.95) 0%, rgba(26, 26, 26, 0.9) 100%);
  border: 2px solid #d4af37;
  border-radius: 20px;
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  box-shadow:
    0 20px 60px rgba(0, 0, 0, 0.8),
    0 0 30px rgba(212, 175, 55, 0.3);
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.3) 0%, rgba(101, 67, 33, 0.2) 100%);
  border: 2px solid #8b4513;
  border-radius: 50%;
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 1;
  transition: all 0.3s ease;
  color: #c9aa6c;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
}

.modal-close:hover {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.3) 0%, rgba(184, 134, 11, 0.2) 100%);
  color: #d4af37;
  border-color: #d4af37;
  transform: scale(1.1);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
}

.modal-close svg {
  width: 20px;
  height: 20px;
  transition: all 0.3s ease;
}

.modal-close:hover svg {
  transform: rotate(90deg);
}

.modal-image {
  height: 300px;
  overflow: hidden;
}

.modal-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.modal-body {
  padding: 2rem;
}

.modal-body h2 {
  font-size: 2rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #d4af37;
  text-shadow:
    0 0 10px rgba(212, 175, 55, 0.8),
    0 0 20px rgba(212, 175, 55, 0.6),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  letter-spacing: 1px;
  text-transform: uppercase;
}

.modal-description {
  font-size: 1.1rem;
  color: #c9aa6c;
  line-height: 1.6;
  margin-bottom: 2rem;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  font-family: 'MedievalSharp', cursive;
  font-style: italic;
  letter-spacing: 0.5px;
}

.modal-section {
  margin-bottom: 2rem;
}

.modal-section h4 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  letter-spacing: 0.5px;
  text-transform: uppercase;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.features-list {
  list-style: none;
  padding: 0;
}

.features-list li {
  color: #c9aa6c;
  margin-bottom: 0.8rem;
  position: relative;
  padding-left: 2rem;
  font-size: 1rem;
  text-shadow:
    0 0 6px rgba(201, 170, 108, 0.7),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  line-height: 1.5;
  font-family: 'MedievalSharp', cursive;
  letter-spacing: 0.3px;
}

.features-list li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #d4af37;
  font-weight: bold;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  font-size: 1.1rem;
}

.modal-actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
}

.btn {
  padding: 0.8rem 1.2rem;
  border: 2px solid #8b4513;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.4) 0%, rgba(101, 67, 33, 0.3) 100%);
  border-radius: 0;
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  font-size: 0.85rem;
  color: #d4af37;
  text-decoration: none;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 3px rgba(0, 0, 0, 0.8);
  letter-spacing: 0.5px;
  text-transform: uppercase;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 150px;
  backdrop-filter: blur(5px);
}

.btn:hover {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #f4d03f;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  border-color: #d4af37;
}

.btn-primary {
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.4) 0%, rgba(101, 67, 33, 0.3) 100%);
  color: #d4af37;
  border-color: #8b4513;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 3px rgba(0, 0, 0, 0.8);
  box-shadow: none;
}

.btn-primary:hover {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #f4d03f;
  border-color: #d4af37;
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
}

.btn-secondary {
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.4) 0%, rgba(101, 67, 33, 0.3) 100%);
  color: #d4af37;
  border-color: #8b4513;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.9),
    1px 1px 3px rgba(0, 0, 0, 0.8);
}

.btn-secondary:hover {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #f4d03f;
  border-color: #d4af37;
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .projects-filter {
    gap: 0.5rem;
  }

  .filter-btn {
    padding: 0.5rem 1rem;
    font-size: 0.9rem;
  }

  .project-overlay {
    padding: 1.5rem 1rem;
  }

  .overlay-title {
    font-size: 1.2rem;
    margin-bottom: 1.2rem;
  }

  .project-links {
    gap: 0.6rem;
    max-width: 100%;
  }

  .project-links-row {
    gap: 0.4rem;
  }

  .project-link {
    padding: 0.7rem 1rem;
    font-size: 0.8rem;
  }

  .project-link-small {
    padding: 0.5rem 0.8rem;
    font-size: 0.7rem;
    min-width: 70px;
    max-width: 100px;
  }

  .modal-overlay {
    padding: 1rem;
  }

  .modal-body {
    padding: 1.5rem;
  }

  .modal-actions {
    flex-direction: column;
  }
}

@keyframes darkSoulsGlow {
  from {
    text-shadow:
      0 0 10px rgba(212, 175, 55, 0.8),
      0 0 20px rgba(212, 175, 55, 0.6),
      2px 2px 4px rgba(0, 0, 0, 0.8);
  }
  to {
    text-shadow:
      0 0 15px rgba(212, 175, 55, 1),
      0 0 30px rgba(212, 175, 55, 0.8),
      3px 3px 6px rgba(0, 0, 0, 0.9);
  }
}
</style>
