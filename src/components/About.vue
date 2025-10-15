<template>
  <section id="apropos" class="about">
    <div class="container">
      <div class="section-header">
        <h2>À propos de moi</h2>
        <p>Découvrez mon parcours et mes compétences en développement web</p>
      </div>

      <div class="about-content">
        <div class="about-text">
          <div class="about-intro">
            <h3>Bonjour ! Je suis Jérémy</h3>
            <p>
              Actuellement en Bachelor de Développement Web, je suis passionné par la création
              d'expériences digitales innovantes et performantes. Mon objectif est de devenir un
              développeur full-stack polyvalent capable de relever tous les défis techniques.
            </p>
            <p>
              J'aime apprendre de nouvelles technologies et me tenir à jour avec les dernières
              tendances du développement web. Chaque projet est pour moi une opportunité
              d'apprentissage et d'amélioration continue.
            </p>
          </div>

          <div class="skills">
            <h4>Mes compétences</h4>
            <div class="skills-grid">
              <div class="skill-category">
                <h5>Frontend & Frameworks</h5>
                <div class="skill-tags">
                  <span class="skill-tag">HTML</span>
                  <span class="skill-tag">React.js</span>
                  <span class="skill-tag">Vue.js</span>
                  <span class="skill-tag">Quasar</span>
                  <span class="skill-tag">Swiper JS</span>
                </div>
              </div>

              <div class="skill-category">
                <h5>Backend & Bases de données</h5>
                <div class="skill-tags">
                  <span class="skill-tag">Python</span>
                  <span class="skill-tag">PHP</span>
                  <span class="skill-tag">Node.js</span>
                  <span class="skill-tag">SQL/NoSQL</span>
                </div>
              </div>

              <div class="skill-category">
                <h5>Outils & Design</h5>
                <div class="skill-tags">
                  <span class="skill-tag">Docker</span>
                  <span class="skill-tag">Unity</span>
                  <span class="skill-tag">Photoshop</span>
                  <span class="skill-tag">WordPress</span>
                  <span class="skill-tag">Webflow</span>
                  <span class="skill-tag">Figma</span>
                  <span class="skill-tag">Notion</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="about-stats">
          <div class="stat-card">
            <div class="stat-number">2+</div>
            <div class="stat-label">Années d'études</div>
          </div>

          <div class="stat-card">
            <div class="stat-number">15+</div>
            <div class="stat-label">Projets réalisés</div>
          </div>

          <div class="stat-card">
            <div class="stat-number">5+</div>
            <div class="stat-label">Technologies maîtrisées</div>
          </div>

          <div class="stat-card">
            <div class="stat-number">100%</div>
            <div class="stat-label">Motivation</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Pas de logique particulière nécessaire pour ce composant
</script>

<style scoped>
.about {
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

.about::before {
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

.about-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 4rem;
  margin-bottom: 4rem;
}

.about-intro h3 {
  font-size: 1.6rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 2rem;
  color: #f4d03f;
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.6);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.about-intro p {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #e6d7a3;
  margin-bottom: 2rem;
  font-family: 'Cormorant Garamond', serif;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.4);
  font-style: italic;
}

.skills {
  margin-top: 3rem;
}

.skills h4 {
  font-size: 1.5rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 2rem;
  color: #f4d03f;
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.6);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.skills-grid {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.skill-category h5 {
  font-size: 1.2rem;
  font-family: 'Cinzel', serif;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: #e6d7a3;
  text-shadow: 0 0 6px rgba(230, 215, 163, 0.5);
  letter-spacing: 0.5px;
  line-height: 1.3;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.skill-tag {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.15) 0%, rgba(184, 134, 11, 0.08) 100%);
  color: #f4d03f;
  padding: 0.8rem 1.5rem;
  border: 1px solid #d4af37;
  border-radius: 8px;
  font-size: 0.9rem;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 500;
  transition: all 0.3s ease;
  text-shadow: 0 0 6px rgba(244, 208, 63, 0.6);
  box-shadow: 0 3px 10px rgba(212, 175, 55, 0.3);
}

.skill-tag:hover {
  transform: translateY(-2px);
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.2) 0%, rgba(184, 134, 11, 0.1) 100%);
  color: #f4d03f;
  text-shadow: 0 0 12px rgba(244, 208, 63, 0.7);
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.4);
  border-color: #f4d03f;
}

.about-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.stat-card {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.1) 0%, rgba(184, 134, 11, 0.05) 100%);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  border: 1px solid rgba(212, 175, 55, 0.3);
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.2);
}

.stat-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(212, 175, 55, 0.3);
  border-color: #f4d03f;
}

.stat-number {
  font-size: 2.5rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #d4af37;
  text-shadow: 0 0 20px rgba(212, 175, 55, 0.6);
  margin-bottom: 0.5rem;
}

.stat-label {
  color: #daa520;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 500;
  font-size: 1rem;
  text-shadow: 0 0 8px rgba(218, 165, 32, 0.4);
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-stats {
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .stat-card {
    padding: 1.5rem;
  }

  .stat-number {
    font-size: 2rem;
  }

  .education {
    padding: 2rem;
  }

  .education-item {
    flex-direction: column;
    gap: 1rem;
  }

  .education-year {
    min-width: auto;
    text-align: left;
  }

  .section-header h2 {
    font-size: 2rem;
  }
}
</style>
