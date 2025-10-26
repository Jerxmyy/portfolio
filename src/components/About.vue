<template>
  <section id="apropos" class="about">
    <div class="container">
      <div class="section-header">
        <h2>À propos de moi</h2>
        <p>Découvrez qui je suis et mes compétences en développement web</p>
      </div>

      <div class="about-content">
        <div class="about-text">
          <div class="about-intro">
            <h3>Créateur d'interfaces & releveur de défis</h3>
            <p>
              Passionné par le développement, je me spécialise dans la création d'interfaces
              modernes et intuitives. Chaque nouveau projet représente pour moi un défi stimulant à
              relever, une opportunité d'explorer de nouvelles approches et de repousser les limites
              de la créativité technique, tout en apprenant de nouvelles technologies, methodes et
              outils.
            </p>
            <p>
              J'adore concevoir des expériences utilisateur exceptionnelles en combinant esthétique
              et fonctionnalité. Mon plaisir réside dans la résolution de problèmes complexes et la
              transformation d'idées abstraites en interfaces concrètes et performantes.
            </p>
            <p>
              Mon objectif ? Continuer à évoluer dans cet univers numérique fascinant, en créant des
              solutions innovantes qui marquent les esprits et en relevant sans cesse de nouveaux
              défis techniques.
            </p>
          </div>
        </div>

        <div class="skills-section">
          <h4>Mon Stack Technique</h4>
          <div class="skills-grid">
            <div class="skill-category">
              <h5>Frontend & Frameworks</h5>
              <div class="skill-tags">
                <span class="skill-tag">HTML5</span>
                <span class="skill-tag">CSS3</span>
                <span class="skill-tag">JavaScript</span>
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
                <span class="skill-tag">SQL</span>
                <span class="skill-tag">NoSQL</span>
                <span class="skill-tag">API REST</span>
              </div>
            </div>

            <div class="skill-category">
              <h5>Outils & Design</h5>
              <div class="skill-tags">
                <span class="skill-tag">Docker</span>
                <span class="skill-tag">Git</span>
                <span class="skill-tag">Unity</span>
                <span class="skill-tag">Photoshop</span>
                <span class="skill-tag">Figma</span>
                <span class="skill-tag">WordPress</span>
                <span class="skill-tag">Webflow</span>
                <span class="skill-tag">Notion</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.about {
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

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-bottom: 4rem;
  align-items: start;
}

.about-text {
  padding-right: 2rem;
}

.about-intro h3 {
  font-size: 1.6rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 2rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  letter-spacing: 0.5px;
  line-height: 1.3;
  text-transform: uppercase;
}

.about-intro p {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #c9aa6c;
  margin-bottom: 2rem;
  font-family: 'MedievalSharp', cursive;
  text-shadow:
    0 0 4px rgba(201, 170, 108, 0.6),
    1px 1px 2px rgba(0, 0, 0, 0.5);
  font-style: italic;
  letter-spacing: 0.5px;
}

.skills-section {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.05) 0%, rgba(139, 69, 19, 0.03) 100%);
  padding: 2.5rem;
  border-radius: 12px;
  border: 1px solid rgba(212, 175, 55, 0.2);
  box-shadow: 0 8px 32px rgba(212, 175, 55, 0.1);
  position: relative;
  overflow: hidden;
}

.skills-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="techPattern" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="10" cy="10" r="1" fill="%23d4af37" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23techPattern)"/></svg>');
  opacity: 0.3;
  pointer-events: none;
}

.skills-section h4 {
  font-size: 1.8rem;
  font-family: 'Cinzel', serif;
  font-weight: 700;
  margin-bottom: 2.5rem;
  color: #d4af37;
  text-shadow:
    0 0 10px rgba(212, 175, 55, 0.8),
    0 0 20px rgba(212, 175, 55, 0.6),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  letter-spacing: 1px;
  line-height: 1.3;
  text-transform: uppercase;
  text-align: center;
  position: relative;
  z-index: 2;
  animation: darkSoulsGlow 4s ease-in-out infinite alternate;
}

.skills-grid {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  position: relative;
  z-index: 2;
}

.skill-category h5 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  letter-spacing: 0.5px;
  line-height: 1.3;
  text-transform: uppercase;
  border-bottom: 2px solid rgba(212, 175, 55, 0.3);
  padding-bottom: 0.5rem;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
}

.skill-tag {
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.15) 0%, rgba(139, 69, 19, 0.1) 100%);
  color: #d4af37;
  padding: 0.6rem 1.2rem;
  border: 2px solid rgba(212, 175, 55, 0.4);
  border-radius: 8px;
  font-size: 0.85rem;
  font-family: 'MedievalSharp', cursive;
  font-weight: 500;
  transition: all 0.4s ease;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.6);
  box-shadow:
    0 4px 12px rgba(212, 175, 55, 0.2),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  text-transform: uppercase;
  letter-spacing: 0.5px;
  position: relative;
  overflow: hidden;
}

.skill-tag::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.2), transparent);
  transition: left 0.6s ease;
}

.skill-tag:hover::before {
  left: 100%;
}

.skill-tag:hover {
  transform: translateY(-3px) scale(1.05);
  background: linear-gradient(135deg, rgba(212, 175, 55, 0.25) 0%, rgba(139, 69, 19, 0.15) 100%);
  color: #f4d03f;
  text-shadow:
    0 0 12px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  box-shadow:
    0 8px 25px rgba(212, 175, 55, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
  border-color: #f4d03f;
}

/* Breakpoints responsives */
@media (max-width: 1200px) {
  .about {
    padding: 80px 30px;
  }

  .about-content {
    gap: 3.5rem;
  }

  .section-header h2 {
    font-size: 2.3rem;
  }
}

@media (max-width: 992px) {
  .about {
    padding: 70px 25px;
  }

  .about-content {
    gap: 3rem;
  }

  .about-intro h3 {
    font-size: 1.4rem;
  }

  .about-intro p {
    font-size: 1.1rem;
  }

  .skills-section h4 {
    font-size: 1.6rem;
  }

  .skill-category h5 {
    font-size: 1.2rem;
  }
}

@media (max-width: 768px) {
  .about {
    padding: 60px 20px;
  }

  .about-content {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }

  .about-text {
    padding-right: 0;
  }

  .about-intro h3 {
    font-size: 1.3rem;
    margin-bottom: 1.5rem;
  }

  .about-intro p {
    font-size: 1rem;
    margin-bottom: 1.5rem;
  }

  .skills-section {
    padding: 2rem;
  }

  .skills-section h4 {
    font-size: 1.4rem;
    margin-bottom: 2rem;
  }

  .skill-category h5 {
    font-size: 1.1rem;
    margin-bottom: 1.2rem;
  }

  .skill-tags {
    gap: 0.6rem;
  }

  .skill-tag {
    padding: 0.5rem 1rem;
    font-size: 0.8rem;
  }

  .section-header h2 {
    font-size: 1.8rem;
    margin-bottom: 1rem;
  }

  .section-header p {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .about {
    padding: 50px 15px;
  }

  .about-content {
    gap: 2rem;
  }

  .about-intro h3 {
    font-size: 1.2rem;
  }

  .about-intro p {
    font-size: 0.95rem;
  }

  .skills-section {
    padding: 1.5rem;
  }

  .skills-section h4 {
    font-size: 1.2rem;
  }

  .skill-category h5 {
    font-size: 1rem;
  }

  .skill-tag {
    padding: 0.4rem 0.8rem;
    font-size: 0.75rem;
  }

  .section-header h2 {
    font-size: 1.6rem;
  }

  .section-header p {
    font-size: 1rem;
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
