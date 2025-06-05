# ChatBot Juridique

> Un assistant conversationnel intelligent spécialisé dans le domaine juridique pour les Junior Entreprises, utilisant l'architecture RAG (Retrieval-Augmented Generation) pour fournir des réponses précises et contextualisées.

## Table des matières

- [Aperçu du projet](#aperçu-du-projet)
- [Architecture](#architecture)
- [Démarrage rapide](#démarrage-rapide)
- [Repositories](#repositories)
- [Documentation](#documentation)
- [État de l'art](#état-de-lart)

---

## Aperçu du projet

### Contexte et motivation

Le domaine juridique nécessite un accès rapide et précis à l'information. Notre ChatBot juridique vise à automatiser les tâches répétitives et à faciliter l'accès aux ressources juridiques.

### Objectifs

#### Fonctionnels
- Réponse automatique aux questions juridiques fréquentes
- Recherche et extraction d'informations dans les documents juridiques
- Orientation vers les textes appropriés
- Explication de procédures et termes juridiques

#### Non fonctionnels
- **Simplicité** : Interface intuitive et accessible
- **Sécurité** : Protection des données sensibles
- **Scalabilité** : Capacité à traiter un grand volume de requêtes
- **Fiabilité** : Réponses précises et vérifiées

---

## Architecture

### Fonctionnement du RAG

```mermaid
flowchart TD
    A["Utilisateur"] --"Requête"--> B["Vectorisation"] 
    A --"Requête"--> C["LLM"]
    B --"Retrieval"--> D[("Base de données vectorielle")]
    D --"Chunks pertinents"--> C
    C --"Réponse"--> A
```

### Architecture globale

L'application suit une architecture microservices orchestrée par Docker Compose :

```mermaid
flowchart TD
    %% Infrastructure Docker
    subgraph INFRA["🐳 Infrastructure Docker"]
        COMPOSE["docker-compose.yml"]
    end
    
    %% Services Backend
    subgraph BACKEND["🔧 Services Backend"]
        MONGO[("🗄MongoDB<br/>Port 27017")]
        SCRAP["Scraping Kiwix<br/>Collecte données"]
        VECTOR["Vectorisation<br/>Pipeline ML"]
        API["API Backend<br/>Port 8000"]
    end
    
    %% Frontend
    subgraph FRONTEND["Interface Utilisateur"]
        WEB["⚛React Frontend<br/>Port 3000"]
    end
    
    %% Flux de données
    COMPOSE --> MONGO
    COMPOSE --> SCRAP
    COMPOSE --> VECTOR
    COMPOSE --> API
    COMPOSE --> WEB
    
    SCRAP --> MONGO
    VECTOR --> MONGO
    API --> MONGO
    WEB --> API
    
    %% Utilisateur
    USER["Utilisateur"] --> WEB
```

### Flux de traitement des données

```mermaid
flowchart LR
    %% Collecte
    A["Sources juridiques<br/>(Kiwix)"] --> B["Scraping"]
    
    %% Traitement
    B --> C["Documents bruts"]
    C --> D["✂Découpage chunks"]
    D --> E["Génération embeddings"]
    E --> F[("🗄Base vectorielle<br/>MongoDB")]
    
    %% Application
    F --> G["Recherche RAG"]
    G --> H["LLM + Context"]
    H --> I["Réponse utilisateur"]
    
    %% Interface
    J["Question utilisateur"] --> G
```

---

## Démarrage rapide

### Prérequis

- Docker et Docker Compose installés
- Git pour cloner le repository

### Lancement de l'application complète

L'ensemble de l'application est orchestré via Docker Compose dans le dossier `infra/`. Cette configuration lance tous les services nécessaires :

```bash
# Cloner le repository
git clone <url-du-repo>
cd chatbot

# Lancer tous les services
cd infra/
docker-compose up -d

# Voir les logs en temps réel
docker-compose logs -f

# Arrêter tous les services
docker-compose down
```

### Services déployés

Le docker-compose lance automatiquement :

1. **MongoDB** (Port 27017) - Base de données principale
2. **Service de scraping** - Collecte des données juridiques depuis Kiwix
3. **Pipeline de vectorisation** - Traitement et vectorisation des documents
4. **API Backend** (Port 8000) - API REST pour le chatbot
5. **Frontend** (Port 3000) - Interface utilisateur React

### Accès aux services

- **Interface utilisateur** : http://localhost:3000
- **API Backend** : http://localhost:8000
- **MongoDB** : localhost:27017 (admin/password)

### Configuration

Les variables d'environnement sont configurées directement dans le `docker-compose.yml`. Pour la production, il est recommandé d'utiliser des fichiers `.env` séparés.

### Développement

Pour le développement local, vous pouvez lancer les services individuellement ou utiliser les volumes montés pour le hot reload du frontend.

---
## Repositories

## Repositories

| Repository | Description | Technologies | Status |
|------------|-------------|--------------|--------|
| **[infra](https://github.com/epf-projet-chatbot/infra)** | Repository principal et orchestration | Docker, Docker Compose | ![Status](https://img.shields.io/badge/status-en%20cours-yellow) |
| **[legal-chatbot-front](https://github.com/epf-projet-chatbot/legal-chatbot-front)** | Interface utilisateur | React, TypeScript, Tailwind | ![Status](https://img.shields.io/badge/status-en%20cours-yellow) |
| **[api](https://github.com/epf-projet-chatbot/api)** | API | FastAPI, Python | ![Status](https://img.shields.io/badge/status-en%20cours-yellow) |
| **[ai](https://github.com/epf-projet-chatbot/ai)** | Modèles IA et RAG | Python, HuggingFace, groq | ![Status](https://img.shields.io/badge/status-à%20faire-red) |
| **[vectorisation](https://github.com/epf-projet-chatbot/vectorisation)** | Gestion des données et vectorisation | Python, MongoDB, HuggingFace, Embeddings | ![Status](https://img.shields.io/badge/status-fait-green) |
| **[docs](https://github.com/epf-projet-chatbot/docs)** | Documentation technique | Markdown | ![Status](https://img.shields.io/badge/status-planifié-blue) |
---

## Etat de l'art

- Travaux existants
    - Chatbots
    - Pipelines
    - Techniques utilisées (Ex: arbre de décision)

### Spécificités des chatbots juridiques (legalbots)
Les chatbots juridiques, représentent une application particulièrement prometteuse de l’IA conversationnelle dans le secteur du droit. Leur état de l’art en 2025 se caractérise par :

1. Automatisation des tâches simples et répétitives

Les legalbots répondent instantanément à des questions juridiques fréquentes, orientent les utilisateurs vers les textes de loi appropriés, expliquent des procédures ou des termes juridiques, et allègent la charge des juristes sur les tâches basiques.

Ils sont utilisés aussi bien en interne (cabinet d’avocats, directions juridiques) qu’en externe (sites web, portails clients).

2. Intégration de modèles avancés (GPT-4 et suivants)

Les legalbots s’appuient sur les modèles de langage les plus récents, capables de réussir des examens professionnels (comme le barreau), garantissant ainsi la qualité et la pertinence des réponses fournies.

Ils peuvent analyser et extraire des informations de documents juridiques complexes (contrats, décisions de justice), facilitant la gestion documentaire à grande échelle.

3. Personnalisation et contextualisation

Certains chatbots juridiques sont conçus pour interroger des bases de données spécifiques (par exemple, tous les articles d’un site juridique ou les forums d’une communauté d’experts), offrant des réponses contextualisées et fiables.

Ils valorisent l’expertise humaine en relayant les questions complexes vers des professionnels, tout en automatisant le tri et la première analyse des demandes.

4. Limites et complémentarité

Les legalbots ne remplacent pas l’expertise humaine pour les situations complexes ou nécessitant une interprétation subtile du droit. Ils servent d’assistants, accélérant l’accès à l’information et la préparation des dossiers, mais la validation finale reste du ressort du professionnel.

5. Exemples d’usages concrets

Assistance à la conformité (compliance), due diligence lors de fusions-acquisitions, analyse de risques, recherche de clauses spécifiques dans des contrats, aide à la rédaction de documents juridiques standards.

Aide à la compréhension du RGPD, de la fiscalité, du droit des sociétés, du droit de la famille, etc., pour les particuliers comme pour les professionnels.


### Exemples

[law.co](https://law.co/) : S'appuie sur le modèle GPT-4 pour aider les personnes travaillant dans le domaine légal à générer leurs documents.
[rasa](https://github.com/RasaHQ/rasa) : Un chatbot opensource 
[wit.ai](https://github.com/wit-ai) : Outil opensource de création et d'entraînement de chatbots disponible en Node.js, Python, Go, Ruby et Unity
