# Dockerized OCR-service Setup

## Pull Images

```bash
docker pull ollama/ollama:latest
docker pull ameurelmoukh/ocr-service
docker pull ameurelmoukh/comparison-service
docker pull ameurelmoukh/api-gateway
```

## Services

- **ollama**: Ollama LLM service with `llama3.2:1b` model
- **ollama-init**: Initializes Ollama and pulls the model
- **ocr**: OCR processing service
- **comparison**: Comparison service using OCR and Ollama
- **api**: API Gateway

## Quick Start

```bash
# Start all services
docker-compose up -d
```

## Endpoints

- **API Gateway**: http://localhost:8080
- **OCR Service**: http://localhost:8000
- **Comparison Service**: http://localhost:8001
- **Ollama Service**: http://localhost:11434

## Request Structure

Send a file and data attributes as **form data**:

```bash
curl -X POST http://localhost:8080/process \
  -F "file=@/path/to/file.pdf" \
  -F "data=value1" \
```

**Form Data Fields:**
- `file`: The file to process (PDF, image, etc.)
- `data`: Additional data attributes (can be multiple fields)

## Response Structure

```json
{
    "extracted_text": "AMEUR ELMOUKH Full Stack javascript php Developer & ameurelmoukh04@gmail.com +212608666579 +212646437992 Tanger, Maroc RÉSUMÉ DU PROFIL Ainsi Que la Gestion Des Bases De Données SQL. EXPÉRIENCE PROFESSIONNELLE Stage Développeur Web Full-Stack (Django, React js,_postgreSQL) VNB-IT - France (Remote) - Juillet 2025 à Sept 2025 (3 mois) Mise en place de nouvelles fonctionnalités, développement du système de parrainage et des statistiques côté backend, amélioration du dashboard et correction des bugs côté front-end, ce qui a amélioré I'expérience utilisateur. Développement backend avec Python/Django, base de données PostgreSQL et React.js pour le front-end. Stage Développeur Web Full-Stack (Symfony / Twig L jQuery). ProxiSoft - Sala al jadida (présentiel) - Avril 2025 à Mai 2025 (1 mois) Contribution à Mise en place d'un ERP incluant des modules de gestion (clients, fournisseurs, produits). Développement backend avec Symfony Intégration frontend (Twig, Ajax, jQuery) PROJETS RÉALISÉS Readyportfolio.com Live Preview Plateforme web permettant aux utilisateurs de créer et partager leur portfolio professionnel en ligne pendant 5min via un lien personnalisé. Mise en place de conteneurs Docker et déploiement sur un VPS pour assurer la scalabilité et la stabilité de I'application. Stack : Laravel, React.js, MySQL, Tailwind CSS, Docker, VPS Ai Road Lien Github SaaS (Laravel/React) de détection de texte IA, Google OAuth, Stripe + Cashier pour les abonnements, génération d'images intégrée. EDUCATION ISMONTIC, Tanger Diplôme de Technicien spécialisé en Développement Web Full-Stack 2023-2025 Lycée Ibn Alkhatib, Salé 2021-2022 Baccalaureat En Sciences Physic Option Francais Mention Bien COMPÉTENCE PROFESSIONNELLE Contrôle De Version : Git et GitHub Developement Back-End : PHP, Symfony, Laravel Les Bases Du Développement Front-End : JS, Reactjs Problem Solving Gestion Des Bases De Données : MySQL, POSTGRESQL RESTful APIs LANGUES",
    "extracted_fields": {
        "full_name": "AMEUR ELMOUKH",
        "degree": "Bachelor of Science in Computer Science",
        "institution": "University Name",
        "endDate": "2025"
    },
    "comparison": {
        "full_name": "match",
        "degree": "partial match",
        "institution": "mismatch",
        "endDate": "match"
    }
}
```
