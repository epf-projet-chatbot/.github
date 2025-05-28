# Création d'un ChatBot juridique

## Répartition des tâches

### Frontend
- Daphné
- Maewenn
- Clément
- Quentin

### Maquettage
- Matthieu
- Romane

### Backend
#### Logique 
- Samy
- Noémie
- Quentin

#### Base de données
- Théo
- Romain

#### NLP
- Alberique
- Pierre-?

#### Modèle IA
- Minh
- Léopold

#### Architecture RAG et LLM
- Guillaume
- Nassim

#### Web
- Gabriel
- Rémi
- Alexandre
- Quentin

## Livrables

- Code source
- Rapport

## Contexte

- Motivations
- Besoin / problématique

## Objetcifs

### Fonctionnels
Les fonctionnalités qu'on implémente dans l'application.

### Non fonctionnels
Ex : Simplicité, sécurité, scalabilité

## Périmètre de fonctionnement

- Pipeline de l'appli

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

## Conception

### Diagrammes

- De classe
- De cas d'utilisation
- Pas de diagramme séquence

### Maquettes graphiques

- Accueil
- Connexion
- Création de compte
- Discussion

### Base de données

On ne choisit pas une base de données relationnelle (SQL) mais plutôt une base de données en NoSQL.

Actuellement la base de données est constituée en majeure partie de PDF qu'il faut convertir en JSON.

## Méthode de travail

- Dashboard: Odoo/Trello
- Diagramme de Gantt
