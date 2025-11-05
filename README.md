# Dauphine Generative AI Project 2025 - 2026

Projet de Support Client (Multi)-Agent pour Entreprise Téléphonique

## 📋 Description du Projet

Système Agentique pour un service client téléphonique fictif **TelecomPlus**. Le système doit répondre aux questions clients en utilisant des documents PDF (FAQ) et des données SQL/XLSX (base de données clients).

## 📊 Tables de Données

Le projet contient **6 tables Excel** dans `data/` :

| Table | Description |
|-------|-------------|
| **clients.xlsx** | Informations clients (nom, prénom, email, téléphone, adresse) |
| **forfaits.xlsx** | Forfaits disponibles (nom, data mensuelle, prix, durée engagement) |
| **abonnements.xlsx** | Abonnements actifs des clients (forfait, dates, statut engagement) |
| **consommation.xlsx** | Consommation mensuelle (data utilisée, minutes, SMS) |
| **factures.xlsx** | Factures clients (montant, statut paiement, échéances) |
| **tickets_support.xlsx** | Tickets de support technique (catégorie, statut, priorité) |

**Documents PDF** (7 fichiers dans `data/pdfs/`) :
- FAQ_Facturation_et_Paiements.pdf
- FAQ_Forfaits_et_Abonnements.pdf
- FAQ_Support_Technique.pdf
- FAQ_Roaming_International.pdf
- FAQ_Compte_Client.pdf
- FAQ_Resiliation_et_Modifications.pdf
- FAQ_Catalogue_Telephones.pdf

## 🔧 Installation et Configuration

### 1. Cloner le Projet

Commencez par cloner le projet sur votre ordinateur :

```bash
git clone https://github.com/BastinFlorian/dauphine-project-iasd-2025
cd dauphine-project-iasd-2025
```

### 2. Créer une Branche de Développement

**Important** : Ne travaillez pas directement sur la branche `main`. Créez votre propre branche :

```bash
# Créer et basculer sur une nouvelle branche
git checkout -b FEATURE/description-de-votre-travail

# Exemple :
git checkout -b FEATURE/multi-agent-rag-system
```

### 3. Workflow Git

Pendant votre développement, utilisez ce workflow :

```bash
# Voir l'état de vos modifications
git status

# Ajouter vos fichiers modifiés
git add .
# Ou ajouter des fichiers spécifiques
git add src/main.py evaluate.py

# Créer un commit avec un message descriptif
git commit -m "feat: implement RAG agent with PDF indexing"

# Pousser votre branche sur GitHub
git push origin FEATURE/description-de-votre-travail
```

**Bonnes pratiques Git** :
- Faites des commits réguliers avec des messages clairs
- Utilisez des messages conventionnels (feat, fix, docs, refactor, etc.)
- Poussez régulièrement votre code pour éviter de perdre votre travail
- Créer des Pull Request et merger le code sur main ensuite, uniquement après validation de votre binôme

## 🚀 Lancer l'Application

Pour vous simplifier la démonstration, une interface a été crée.

Pour la lancer sur votre ordinateur, après avoir créé un environnement virtuel, éxécutez les commandes suivantes:

```bash
pip install -r requirements.txt
streamlit run app.py
```
L'interface Streamlit s'ouvrira dans votre navigateur.
Pour l'instant, une réponse basique est donnée.
Votre travail est d'améliorer la réponse afin de la rendre pertinente pour le cas d'usage en question.

### Exemple:
Par exemple, voici les réponses attendues pour deux questions distinctes:

**Q. Quels modes de paiement acceptez-vous ?**

R. Nous acceptons les paiements par carte bancaire, prélèvement automatique, virement bancaire et PayPal. Le prélèvement automatique garantit de ne jamais manquer une échéance.

**Q. Y a-t-il des frais de résiliation si je suis engagé ?**

R. Si vous êtes encore en période d'engagement, des frais égaux au montant des mensualités restantes peuvent s'appliquer. Si vous êtes hors engagement (après 12 ou 24 mois), la résiliation est gratuite.

Pour evaluer votre agent, il faudra modifier le script d'évaluation (créé par défaut):

```python
python evaluate.py
```

## 🎯 Travail à Réaliser

### 1. Créer un Agent IA

Développez un système capable de répondre aux questions clients à paartir de différentes données :
- **RAG** : Recherche dans les documents PDF
- **SQL ou PandaDataframeTool** : Requêtes sur les tables de données
- **Orchestration** : Coordination des agents selon la question

Vous pouvez vous inspirer de l'architecture de dossier [suivante](https://docs.langchain.com/oss/python/langgraph/application-structure) pour construire votre solution

### 2. Créer un Script d'Évaluation

Créez `evaluate.py` pour évaluer votre système :
- Charger les questions depuis `data/evaluation_questions.xlsx` (25 questions)
- Exécuter votre agent sur chaque question
- Comparer les réponses générées aux réponses attendues
- Calculer un score (utilisez un LLM-as-a-judge pour l'évaluation)

### 3. Documenter votre Travail

Le README.md de votre projet doit détailler :
- Architecture de votre système agentique
- Choix techniques et justifications
- Instructions d'installation et d'exécution
- Résultats d'évaluation obtenus

## 📝 Modalités de Rendu

### Deadline
**14 décembre 2025 - 23h59**

### Format de Rendu
- Code hébergé sur **GitHub**
- Lien du repository à envoyer avant la deadline

### Soutenance

**Format** :
- **Pas de slides ou présentation PowerPoint demandée**
- Démonstration en direct sur votre ordinateur (vérifier que vous n'avez pas de problème pour partager votre écran lors d'une réunion Teams)
- Questions/réponses sur le code et les choix d'architecture

**Déroulement** (environ 15 minutes) :
1. **Démonstration**: Montrer l'application fonctionnelle
2. **Questions du professeur** : Tester votre Agent IA avec de nouvelles questions
3. **Outil de monitoring**: Présenter les traces et métriques (Langfuse/Langsmith/MLflow)
4. **Discussion technique** : Expliquer les choix d'implémentation

## 📊 Critères d'Évaluation

### 1. Performance et Pertinence (30%)
- **Dataset d'entraînement** : Qualité des réponses sur les 25 questions d'évaluation
- **Généralisation** : Capacité à répondre à des questions inconnues posées lors de la soutenance
- **Précision** : Justesse des informations extraites (documents PDF et données SQL)

### 2. Qualité du Code et Bonnes Pratiques (30%)
- **Clarté et documentation** : Code lisible, commenté, avec docstrings
- **Structure du projet** : Organisation logique des fichiers et modules
- **Prompts** : Qualité et précision des prompts utilisés
- **Évaluation** : Script `evaluate.py` fonctionnel avec métriques pertinentes

### 3. Architecture Agentique (25%)
- **Complexité** : Sophistication de l'approche choisie (simple agent vs multi-agent)
- **Justification** : Pertinence des choix techniques (RAG, SQL, orchestration)
- **Efficacité** : Performance et temps de réponse du système

### 4. Monitoring et Auditabilité (15%)
- **Traçabilité** : Utilisation d'un outil de monitoring (Langfuse, Langsmith, ou MLflow)
- **Métriques** : Suivi des appels LLM, coûts, latences, erreurs
- **Démonstrabilité** : Capacité à montrer les traces lors de la soutenance

### Bonus : Simplicité
- Solutions élégantes et minimalistes seront valorisées
- Éviter la complexité inutile (over-engineering)

---

**Exemples d'étapes à réaliser**:
- Indexer les documents PDFs dans une base vecteur en local
- Exploiter les fichier excels en constituant des outils accessibles au LLM
- Réaliser une architecture Agentique adaptée pour fournir des réponses pertinentes
- Evaluer votre agent en utilisant les Questions/Réponses de référence listées dans `evaluation_question.xlsx`
- Documenter et soigner votre code pour respecter les conventions PEP8, Flake8, Mypy, Pylint, ou toute bonne pratiques de code

**Université Paris Dauphine - IASD 2025-2026**
