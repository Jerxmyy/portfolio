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
              <div class="project-links">
                <a :href="project.demo" target="_blank" class="project-link" v-if="project.demo">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path
                      d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"
                    />
                  </svg>
                  Voir le projet
                </a>
                <a
                  :href="project.github"
                  target="_blank"
                  class="project-link"
                  v-if="project.github"
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
              Code source
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

const categories = ['Tous', 'Frontend', 'Full-stack', 'Mobile']

const projects = [
  {
    id: 1,
    title: 'E-commerce Vue.js',
    description: 'Application e-commerce complète avec panier, paiement et gestion des commandes.',
    image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=500&h=300&fit=crop',
    category: 'Frontend',
    technologies: ['Vue.js', 'Vuex', 'CSS3', 'API REST'],
    demo: '#',
    github: '#',
    features: [
      'Interface utilisateur responsive',
      "Gestion du panier d'achat",
      'Système de paiement sécurisé',
      'Gestion des commandes',
      'Recherche et filtres avancés',
    ],
  },
  {
    id: 2,
    title: 'Blog Personnel',
    description: 'Blog personnel avec système de gestion de contenu et authentification.',
    image: 'https://images.unsplash.com/photo-1486312338219-ce68d2c6f44d?w=500&h=300&fit=crop',
    category: 'Full-stack',
    technologies: ['Node.js', 'Express', 'MongoDB', 'React'],
    demo: '#',
    github: '#',
    features: [
      "Système d'authentification",
      'Gestion des articles',
      'Commentaires et likes',
      "Interface d'administration",
      'API REST complète',
    ],
  },
  {
    id: 3,
    title: 'Application Météo',
    description: 'Application météo en temps réel avec géolocalisation et prévisions.',
    image: 'https://images.unsplash.com/photo-1504608524841-42fe6f032b4b?w=500&h=300&fit=crop',
    category: 'Frontend',
    technologies: ['JavaScript', 'API', 'CSS3', 'HTML5'],
    demo: '#',
    github: '#',
    features: [
      'Géolocalisation automatique',
      'Prévisions 7 jours',
      'Interface intuitive',
      'Données en temps réel',
      'Design responsive',
    ],
  },
  {
    id: 4,
    title: 'Gestion de Tâches',
    description: 'Application de gestion de tâches avec équipes et notifications.',
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=500&h=300&fit=crop',
    category: 'Full-stack',
    technologies: ['Vue.js', 'Node.js', 'Socket.io', 'MySQL'],
    demo: '#',
    github: '#',
    features: [
      'Gestion des tâches par équipe',
      'Notifications en temps réel',
      'Système de priorités',
      'Historique des activités',
      'Interface collaborative',
    ],
  },
  {
    id: 5,
    title: 'Portfolio Créatif',
    description: 'Portfolio interactif avec animations et galerie de projets.',
    image: 'https://images.unsplash.com/photo-1467232004584-a241de8bcf5d?w=500&h=300&fit=crop',
    category: 'Frontend',
    technologies: ['Vue.js', 'GSAP', 'Sass', 'Webpack'],
    demo: '#',
    github: '#',
    features: [
      'Animations fluides',
      'Galerie interactive',
      'Design moderne',
      'Performance optimisée',
      'Responsive design',
    ],
  },
  {
    id: 6,
    title: 'App Mobile React Native',
    description: 'Application mobile de fitness avec suivi des exercices et statistiques.',
    image: 'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=500&h=300&fit=crop',
    category: 'Mobile',
    technologies: ['React Native', 'Redux', 'Firebase', 'Expo'],
    demo: '#',
    github: '#',
    features: [
      'Suivi des exercices',
      'Statistiques détaillées',
      'Synchronisation cloud',
      'Interface native',
      'Notifications push',
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
  background: linear-gradient(
    135deg,
    #0c0c0c 0%,
    #1a1a1a 25%,
    #2d1b1b 50%,
    #1a1a1a 75%,
    #0c0c0c 100%
  );
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
  color: #f4d03f;
  text-shadow: 0 0 15px rgba(244, 208, 63, 0.6);
  margin-bottom: 1.5rem;
  animation: goldenGlow 3s ease-in-out infinite alternate;
  letter-spacing: 1px;
  line-height: 1.2;
}

.section-header p {
  font-size: 1.3rem;
  color: #e6d7a3;
  max-width: 700px;
  margin: 0 auto;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.5);
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  line-height: 1.6;
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
  border: 2px solid #d4af37;
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.15) 0%, rgba(184, 134, 11, 0.08) 100%);
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.4s ease;
  font-family: 'Cinzel', serif;
  font-weight: 500;
  font-size: 1rem;
  color: #e6d7a3;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.5);
  letter-spacing: 0.5px;
}

.filter-btn:hover {
  border-color: #f4d03f;
  color: #f4d03f;
  background: linear-gradient(135deg, rgba(244, 208, 63, 0.2) 0%, rgba(212, 175, 55, 0.1) 100%);
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.7);
  transform: translateY(-2px);
}

.filter-btn.active {
  background: linear-gradient(135deg, #d4af37 0%, #b8860b 100%);
  color: #0c0c0c;
  border-color: #f4d03f;
  text-shadow: none;
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.3);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
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
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.9) 0%, rgba(184, 134, 11, 0.8) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.project-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.1) 0%, rgba(184, 134, 11, 0.05) 100%);
  color: #d4af37;
  text-decoration: none;
  border-radius: 25px;
  font-weight: 600;
  transition: all 0.3s ease;
  border: 1px solid #d4af37;
}

.project-link:hover {
  background: linear-gradient(135deg, #d4af37 0%, #b8860b 100%);
  color: #0c0c0c;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.3);
}

.project-content {
  padding: 1.5rem;
}

.project-content h3 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #f4d03f;
  text-shadow: 0 0 10px rgba(244, 208, 63, 0.6);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.project-content p {
  color: #e6d7a3;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  font-size: 1.1rem;
  font-family: 'Cormorant Garamond', serif;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.4);
  font-style: italic;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.2) 0%, rgba(184, 134, 11, 0.1) 100%);
  color: #f4d03f;
  padding: 0.6rem 1rem;
  border: 1px solid rgba(212, 175, 55, 0.5);
  border-radius: 8px;
  font-size: 0.9rem;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 500;
  text-shadow: 0 0 6px rgba(244, 208, 63, 0.6);
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.25) 0%, rgba(184, 134, 11, 0.15) 100%);
  color: #f4d03f;
  border-color: #f4d03f;
  text-shadow: 0 0 10px rgba(244, 208, 63, 0.7);
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
  background: white;
  border-radius: 20px;
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.1);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 1;
  transition: background 0.3s ease;
}

.modal-close:hover {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.2) 0%, rgba(184, 134, 11, 0.1) 100%);
  color: #f4d03f;
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
  color: #f4d03f;
  text-shadow: 0 0 10px rgba(244, 208, 63, 0.6);
}

.modal-description {
  font-size: 1.1rem;
  color: #e6d7a3;
  line-height: 1.6;
  margin-bottom: 2rem;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.4);
}

.modal-section {
  margin-bottom: 2rem;
}

.modal-section h4 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #f4d03f;
  text-shadow: 0 0 8px rgba(244, 208, 63, 0.6);
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
  color: #e6d7a3;
  margin-bottom: 0.8rem;
  position: relative;
  padding-left: 2rem;
  font-size: 1rem;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.4);
  line-height: 1.5;
}

.features-list li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #d4af37;
  font-weight: bold;
  text-shadow: 0 0 8px rgba(212, 175, 55, 0.6);
}

.modal-actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
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
</style>
