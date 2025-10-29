# Portfolio Jérémy - Développeur Front-end & Creative Developer

Portfolio personnel moderne et interactif présentant mes compétences en développement web, mes projets et mon parcours professionnel.

## 🎯 À propos

Ce portfolio est conçu pour mettre en valeur mes compétences en tant que développeur front-end et creative developer. Il présente une interface unique avec un design inspiré de l'esthétique médiévale/fantasy, combinant modernité et créativité technique.

## ✨ Fonctionnalités

- **Section Hero** : Animation de texte typewriter avec effet de frappe dynamique
- **À propos** : Présentation personnelle et stack technique complet
- **Projets** : Galerie interactive avec système de filtres par catégorie (Frontend, Backend, Full-stack)
- **Modales de projets** : Détails enrichis pour chaque projet avec liens GitHub et démos
- **Contact** : Formulaire de contact avec validation et messages d'état
- **Design responsive** : Adaptation complète pour tous les écrans (mobile, tablette, desktop)
- **Animations** : Effets visuels et transitions fluides pour une expérience utilisateur optimale
- **Navigation fluide** : Défilement automatique vers les sections avec indicateur de section active

## 🛠️ Technologies utilisées

### Frontend

- **Vue.js 3** - Framework JavaScript progressif
- **Vite** - Outil de build moderne et rapide
- **Three.js** - Bibliothèque 3D pour animations avancées
- **CSS3** - Styles avec animations et effets visuels
- **Pinia** - Gestion d'état

### Outils de développement

- **ESLint** - Linter pour maintenir la qualité du code
- **Prettier** - Formatage automatique du code

## 📁 Structure du projet

```
portfolio_jeremy/
├── public/
│   ├── image-projet/        # Images des projets
│   └── logo*.png            # Logos
├── src/
│   ├── assets/              # Styles globaux et ressources
│   ├── components/          # Composants Vue
│   │   ├── About.vue        # Section À propos
│   │   ├── Contact.vue      # Section Contact avec formulaire
│   │   ├── Footer.vue       # Pied de page
│   │   ├── Header.vue       # En-tête avec navigation
│   │   ├── Projects.vue     # Galerie de projets
│   │   └── icons/           # Icônes SVG
│   ├── stores/              # Store Pinia
│   ├── App.vue              # Composant principal
│   └── main.js              # Point d'entrée de l'application
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

## 🚀 Installation et démarrage

### Prérequis

- Node.js version `^20.19.0` ou `>=22.12.0`
- npm ou yarn

### Installation

```bash
# Cloner le dépôt (ou télécharger le projet)
git clone https://github.com/Jerxmyy/portfolio
cd portfolio_jeremy

# Installer les dépendances
npm install
```

### Développement

```bash
# Lancer le serveur de développement
npm run dev
```

Le site sera accessible sur `http://localhost:5173` (ou le port indiqué par Vite).

### Production

```bash
# Construire le projet pour la production
npm run build
```

Les fichiers optimisés seront générés dans le dossier `dist/`.

### Prévisualisation de la build

```bash
# Prévisualiser la version de production
npm run preview
```

### Qualité du code

```bash
# Linter le code
npm run lint

# Formater le code avec Prettier
npm run format
```

## 📱 Sections du site

### 🏠 Accueil (Hero)

- Animation de texte dynamique
- Présentation professionnelle
- Boutons d'action vers projets et contact
- Animation de code en arrière-plan

### 👤 À propos

- Description personnelle et objectifs
- Stack technique complet organisé par catégories :
  - Frontend & Frameworks
  - Backend & Bases de données
  - Outils & Design

### 💼 Projets

- 4 projets présentés avec filtres par catégorie
- Chaque projet inclut :
  - Image de présentation
  - Description
  - Technologies utilisées
  - Liens vers démo et code source (GitHub)
  - Modale détaillée avec fonctionnalités

**Projets présentés :**

- Hub Gaming Pop Corn 2024
- Food Truck Holly Thai
- PixelBay
- Musée Explorer

### 📧 Contact

- Formulaire de contact avec validation
- Informations de contact (email, téléphone, localisation)
- Liens vers réseaux sociaux (GitHub, LinkedIn)
- Feedback visuel lors de l'envoi

## 🎨 Design

Le design s'inspire d'une esthétique médiévale/fantasy avec :

- Palette de couleurs dorées et sombres (#d4af37, #8b4513, #c9aa6c)
- Typographie élégante (Cinzel, MedievalSharp, Uncial Antiqua)
- Effets de lueur et ombres pour créer de la profondeur
- Animations fluides et transitions soignées

## 📝 Configuration IDE recommandée

- **VS Code** avec l'extension [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- **Désactiver Vetur** si installé (conflit avec Volar)

## 🌐 Configuration navigateur

Pour une meilleure expérience de développement :

### Chrome / Edge / Brave

- [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
- [Activer Custom Object Formatter](http://bit.ly/object-formatters)

### Firefox

- [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
- [Activer Custom Object Formatter](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## 📄 Licence

Ce projet est privé et personnel.

## 📞 Contact

- **Email** : jeremy.chambon@mail-esd.com
- **Téléphone** : +33 7 66 14 55 88
- **Localisation** : Paris, France
- **GitHub** : [@Jerxmyy](https://github.com/Jerxmyy)
- **LinkedIn** : [Jeremy Chambon](www.linkedin.com/in/jeremy-chambon-a50aaa29a)
