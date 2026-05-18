# 🎓 UniTime - Plateforme Intelligente de Gestion des Emplois du Temps

**UniTime** est une solution web complète développée pour répondre aux défis de la digitalisation universitaire. Conçue spécifiquement pour la **Faculté des Sciences et Techniques de Tanger (FSTT)**, elle vise à remplacer la gestion manuelle complexe par un système automatisé et sans erreur.

Ce projet ne se contente pas de digitaliser un processus papier : il introduit une couche d'intelligence artificielle locale (**NEON**) pour assister les administrateurs et les étudiants au quotidien.

## 🌟 Pourquoi UniTime ?

La gestion des emplois du temps est un casse-tête logistique (conflits de salles, indisponibilités des profs, rattrapages). UniTime résout ces problèmes grâce à trois piliers :
1.  **Automatisation** : Un moteur algorithmique (Constraint Engine) génère des plannings sans conflits en quelques secondes.
2.  **Temps Réel** : Toute modification est instantanément visible par les milliers d'étudiants concernés.
3.  **Intelligence Artificielle** : Un assistant conversationnel intégré répond aux questions vocales ou textuelles sur l'emploi du temps.

## 🚀 Fonctionnalités Détaillées

### 🛡️ Espace Administrateur (La Tour de Contrôle)
* **Génération Automatique** : Lancez l'algorithme qui place intelligemment les cours, TD et TP en respectant les capacités des salles et les vœux des enseignants.
* **Gestion des Conflits** : Le système empêche physiquement la double réservation d'une salle ou d'un enseignant.
* **Statistiques** : Visualisez le taux d'occupation des locaux pour optimiser les ressources.
* **Exports** : Téléchargez les emplois du temps officiels en PDF ou Image PNG en un clic.

### 👨‍🏫 Espace Enseignant
* **Agenda Personnel** : Vue filtrée uniquement sur ses propres cours.
* **Workflow de Réservation** : Demandez un créneau de rattrapage directement via l'application. L'admin reçoit la demande et la valide.
* **Gestion d'Absence** : Signalez une indisponibilité future pour que l'algorithme ne vous place pas de cours ce jour-là.

### 🎓 Espace Étudiant
* **Consultation Ciblée** : L'étudiant voit automatiquement le planning de sa filière et de son groupe (ex: LST AD - Groupe 1).
* **Recherche de Salles** : Besoin d'une salle libre pour réviser ? Un moteur de recherche trouve les locaux vacants en temps réel.

### 🤖 NEON AI (Assistant Intelligent)
* Chatbot basé sur **Llama 3** (Ollama) tournant localement (Confidentialité totale des données).
* Supporte les commandes vocales et répond à l'oral.
* "Conscient du contexte" : Il sait qui est connecté et peut analyser les données de la page.

## 🛠️ Stack Technique

Ce projet respecte une architecture Microservices moderne et conteneurisée :

* **Frontend** : React 18, TypeScript, Vite, TailwindCSS (Design Responsive & Dark Mode).
* **Backend** : Python 3.12, FastAPI (Performance & Validation stricte).
* **Base de Données** : PostgreSQL 15 (Relationnelle).
* **IA / LLM** : Ollama exécutant le modèle Llama 3.
* **DevOps** : Docker & Docker Compose pour un déploiement iso-fonctionnel.

## 📦 Installation et Démarrage

Prérequis : Avoir **Docker Desktop** installé et lancé.

1.  **Cloner le projet**
    ```bash
    git clone [https://github.com/manalrhoni/UniTime.git](https://github.com/manalrhoni/UniTime.git)
    cd UniTime
    ```

2.  **Lancer l'application**
    Cette commande construit les conteneurs et lance tous les services.
    ```bash
    docker-compose up --build
    ```

3.  **Initialiser la Base de Données (Données de test)**
    *Important : Cette commande remplit la base de données locale avec les utilisateurs de démonstration.*
    ```bash
    docker-compose exec backend python app/remplir_db.py
    ```

4.  **Activer l'IA (Une seule fois)**
    Télécharger le modèle Llama 3 dans le conteneur (environ 4 Go).
    ```bash
    docker-compose exec unitime_ollama ollama run llama3
    ```

## 🌐 Accès à l'application

Ouvrez votre navigateur sur : **http://localhost:5173**

### 🔑 Identifiants de Démonstration (Environnement Local)
*Ces comptes sont générés localement sur votre machine pour tester l'application. Ils sont sans danger.*

| Rôle | Email | Mot de passe | Description |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@unitime.ma` | `admin123` | Accès complet, génération et validation. |
| **Enseignant** | `prof@unitime.ma` | `prof123` | Peut réserver des salles et voir son planning. |
| **Étudiant** | `student@unitime.ma` | `student123` | Consultation simple (Vue LST AD). |

