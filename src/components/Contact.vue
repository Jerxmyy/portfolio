<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="section-header">
        <h2>Contactez-moi</h2>
        <p>Une idée de projet ? N'hésitez pas à me contacter !</p>
      </div>

      <div class="contact-content">
        <div class="contact-info">
          <h3>Parlons de votre projet</h3>
          <p>
            Je suis toujours intéressé par de nouveaux défis et opportunités. Que ce soit pour un
            projet freelance, une alternance, ou simplement pour discuter de développement web,
            n'hésitez pas à me contacter !
          </p>

          <div class="contact-methods">
            <div class="contact-method">
              <div class="contact-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"
                  />
                </svg>
              </div>
              <div class="contact-details">
                <h4>Email</h4>
                <p>jeremy.chambon@mail-esd.com</p>
              </div>
            </div>

            <div class="contact-method">
              <div class="contact-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"
                  />
                </svg>
              </div>
              <div class="contact-details">
                <h4>Téléphone</h4>
                <p>+33 7 66 14 55 88</p>
              </div>
            </div>

            <div class="contact-method">
              <div class="contact-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"
                  />
                </svg>
              </div>
              <div class="contact-details">
                <h4>Localisation</h4>
                <p>Paris, France</p>
              </div>
            </div>
          </div>

          <div class="social-links">
            <h4>Suivez-moi</h4>
            <div class="social-icons">
              <a href="https://github.com/Jerxmyy" class="social-link" target="_blank">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
                GitHub
              </a>
              <a
                href="www.linkedin.com/in/jeremy-chambon-a50aaa29a"
                class="social-link"
                target="_blank"
              >
                <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                  />
                </svg>
                LinkedIn
              </a>
            </div>
          </div>
        </div>

        <div class="contact-form-container">
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-group">
              <label for="name">Nom complet</label>
              <input
                type="text"
                id="name"
                v-model="form.name"
                required
                :class="{ error: errors.name }"
              />
              <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
            </div>

            <div class="form-group">
              <label for="email">Email</label>
              <input
                type="email"
                id="email"
                v-model="form.email"
                required
                :class="{ error: errors.email }"
              />
              <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
            </div>

            <div class="form-group">
              <label for="subject">Sujet</label>
              <input
                type="text"
                id="subject"
                v-model="form.subject"
                required
                :class="{ error: errors.subject }"
              />
              <span v-if="errors.subject" class="error-message">{{ errors.subject }}</span>
            </div>

            <div class="form-group">
              <label for="message">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                required
                :class="{ error: errors.message }"
              ></textarea>
              <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
            </div>

            <button type="submit" class="btn btn-primary submit-btn" :disabled="isSubmitting">
              <span v-if="!isSubmitting">Envoyer le message</span>
              <span v-else>Envoi en cours...</span>
            </button>
          </form>

          <div v-if="submitStatus" class="submit-status" :class="submitStatus.type">
            <div class="status-icon">
              <svg
                v-if="submitStatus.type === 'success'"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="currentColor"
              >
                <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z" />
              </svg>
              <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"
                />
              </svg>
            </div>
            <p>{{ submitStatus.message }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const errors = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const isSubmitting = ref(false)
const submitStatus = ref(null)

const validateForm = () => {
  // Reset errors
  Object.keys(errors).forEach((key) => {
    errors[key] = ''
  })

  let isValid = true

  if (!form.name.trim()) {
    errors.name = 'Le nom est requis'
    isValid = false
  }

  if (!form.email.trim()) {
    errors.email = "L'email est requis"
    isValid = false
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
    errors.email = "Format d'email invalide"
    isValid = false
  }

  if (!form.subject.trim()) {
    errors.subject = 'Le sujet est requis'
    isValid = false
  }

  if (!form.message.trim()) {
    errors.message = 'Le message est requis'
    isValid = false
  } else if (form.message.trim().length < 10) {
    errors.message = 'Le message doit contenir au moins 10 caractères'
    isValid = false
  }

  return isValid
}

const submitForm = async () => {
  if (!validateForm()) {
    return
  }

  isSubmitting.value = true
  submitStatus.value = null

  try {
    // Simulation d'envoi d'email
    await new Promise((resolve) => setTimeout(resolve, 2000))

    // Ici, vous pourriez intégrer un service comme EmailJS, Formspree, ou votre propre API
    console.log('Formulaire soumis:', form)

    submitStatus.value = {
      type: 'success',
      message: 'Message envoyé avec succès ! Je vous répondrai dans les plus brefs délais.',
    }

    // Reset form
    Object.keys(form).forEach((key) => {
      form[key] = ''
    })
  } catch (error) {
    submitStatus.value = {
      type: 'error',
      message: "Erreur lors de l'envoi du message. Veuillez réessayer.",
    }
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 40px;
  position: relative;
  overflow: hidden;
  width: 100%;
  max-width: none;
  margin: 0;
  box-sizing: border-box;
}

.contact::before {
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

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-info h3 {
  font-size: 1.8rem;
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
}

.contact-info p {
  font-size: 1.1rem;
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

.contact-methods {
  margin-bottom: 3rem;
}

.contact-method {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.contact-icon {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #d4af37 0%, #b8860b 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #0c0c0c;
  flex-shrink: 0;
  box-shadow: 0 4px 15px rgba(212, 175, 55, 0.3);
}

.contact-details h4 {
  font-size: 1.2rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.contact-details p {
  color: #c9aa6c;
  margin: 0 0 0.8rem 0;
  font-size: 1rem;
  font-family: 'MedievalSharp', cursive;
  text-shadow:
    0 0 4px rgba(201, 170, 108, 0.6),
    1px 1px 2px rgba(0, 0, 0, 0.5);
  letter-spacing: 0.5px;
}

.social-links h4 {
  font-size: 1.3rem;
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.social-icons {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  background: linear-gradient(135deg, rgba(139, 69, 19, 0.2) 0%, rgba(101, 67, 33, 0.1) 100%);
  color: #d4af37;
  text-decoration: none;
  border-radius: 0;
  font-family: 'MedievalSharp', cursive;
  font-weight: 400;
  transition: all 0.3s ease;
  border: 2px solid #8b4513;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  text-shadow:
    0 0 6px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.6);
}

.social-link:hover {
  background: linear-gradient(135deg, #8b4513 0%, #654321 100%);
  color: #f4d03f;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(139, 69, 19, 0.5);
  text-shadow:
    0 0 10px rgba(244, 208, 63, 1),
    2px 2px 4px rgba(0, 0, 0, 0.8);
  border-color: #d4af37;
}

.contact-form-container {
  background: linear-gradient(135deg, rgba(12, 12, 12, 0.9) 0%, rgba(26, 26, 26, 0.8) 100%);
  padding: 2.5rem;
  border-radius: 15px;
  border: 2px solid #d4af37;
  box-shadow: 0 8px 25px rgba(212, 175, 55, 0.2);
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  font-family: 'Cinzel', serif;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #d4af37;
  text-shadow:
    0 0 6px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.form-group input,
.form-group textarea {
  padding: 1.2rem;
  border: 2px solid #8b4513;
  border-radius: 0;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  background: rgba(12, 12, 12, 0.9);
  color: #c9aa6c;
  font-family: 'MedievalSharp', cursive;
  text-shadow:
    0 0 4px rgba(201, 170, 108, 0.6),
    1px 1px 2px rgba(0, 0, 0, 0.5);
  line-height: 1.6;
  letter-spacing: 0.5px;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #d4af37;
  box-shadow: 0 0 20px rgba(212, 175, 55, 0.4);
  background: rgba(12, 12, 12, 0.95);
  color: #d4af37;
  text-shadow:
    0 0 8px rgba(212, 175, 55, 0.8),
    1px 1px 2px rgba(0, 0, 0, 0.7);
}

.form-group input.error,
.form-group textarea.error {
  border-color: #e74c3c;
}

.error-message {
  color: #e74c3c;
  font-size: 0.9rem;
  margin-top: 0.25rem;
}

.submit-btn {
  align-self: flex-start;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  margin-top: 1rem;
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.submit-status {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  border-radius: 10px;
  margin-top: 1rem;
}

.submit-status.success {
  background: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.submit-status.error {
  background: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.status-icon {
  flex-shrink: 0;
}

/* Breakpoints responsives */
@media (max-width: 1200px) {
  .contact {
    padding: 80px 30px;
  }

  .contact-content {
    gap: 3.5rem;
  }

  .section-header h2 {
    font-size: 2.3rem;
  }
}

@media (max-width: 992px) {
  .contact {
    padding: 70px 25px;
  }

  .contact-content {
    gap: 3rem;
  }

  .contact-info h3 {
    font-size: 1.6rem;
  }

  .contact-info p {
    font-size: 1rem;
  }

  .contact-form-container {
    padding: 2rem;
  }

  .section-header h2 {
    font-size: 2.1rem;
  }
}

@media (max-width: 768px) {
  .contact {
    padding: 60px 20px;
  }

  .contact-content {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }

  .contact-info h3 {
    font-size: 1.4rem;
    margin-bottom: 1.2rem;
  }

  .contact-info p {
    font-size: 0.95rem;
    margin-bottom: 1.5rem;
  }

  .contact-method {
    margin-bottom: 1.2rem;
  }

  .contact-icon {
    width: 45px;
    height: 45px;
  }

  .contact-details h4 {
    font-size: 1.1rem;
  }

  .contact-details p {
    font-size: 0.9rem;
  }

  .social-links h4 {
    font-size: 1.2rem;
    margin-bottom: 1.2rem;
  }

  .contact-form-container {
    padding: 1.5rem;
  }

  .form-group label {
    font-size: 0.9rem;
  }

  .form-group input,
  .form-group textarea {
    padding: 1rem;
    font-size: 1rem;
  }

  .submit-btn {
    padding: 0.8rem 1.5rem;
    font-size: 1rem;
  }

  .social-icons {
    flex-direction: column;
    gap: 0.8rem;
  }

  .social-link {
    justify-content: center;
    padding: 0.6rem 1rem;
    font-size: 0.9rem;
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
  .contact {
    padding: 50px 15px;
  }

  .contact-content {
    gap: 2rem;
  }

  .contact-info h3 {
    font-size: 1.3rem;
  }

  .contact-info p {
    font-size: 0.9rem;
  }

  .contact-method {
    margin-bottom: 1rem;
  }

  .contact-icon {
    width: 40px;
    height: 40px;
  }

  .contact-details h4 {
    font-size: 1rem;
  }

  .contact-details p {
    font-size: 0.85rem;
  }

  .social-links h4 {
    font-size: 1.1rem;
  }

  .contact-form-container {
    padding: 1.2rem;
  }

  .form-group label {
    font-size: 0.85rem;
  }

  .form-group input,
  .form-group textarea {
    padding: 0.8rem;
    font-size: 0.9rem;
  }

  .submit-btn {
    padding: 0.7rem 1.2rem;
    font-size: 0.9rem;
  }

  .social-link {
    padding: 0.5rem 0.8rem;
    font-size: 0.85rem;
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
