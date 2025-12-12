# Projet 3 - Prédiction des Émissions de CO2 des Bâtiments de Seattle

## 📋 Description du Projet

Ce projet s'inscrit dans le cadre de la formation Data Science & Machine Learning d'OpenClassrooms. L'objectif est d'aider la ville de Seattle à atteindre son ambition de neutralité carbone d'ici 2050 en prédisant les émissions de CO2 et la consommation énergétique des bâtiments non résidentiels.

**Contexte :** Des relevés minutieux ont été effectués en 2016 sur les bâtiments de Seattle. Ces relevés étant coûteux, nous souhaitons développer un modèle prédictif basé sur les données structurelles des bâtiments (taille, usage, date de construction, localisation géographique, etc.) pour estimer les émissions et la consommation des bâtiments non encore mesurés.

## 🎯 Objectifs

1. **Analyse exploratoire** : Faire ressortir des insights clés sur les différents bâtiments
2. **Modélisation supervisée** : Tester différents modèles pour prédire la consommation énergétique
3. **Interprétation** : Déterminer les facteurs principaux impactant le modèle sélectionné

## 📊 Dataset

- **Source** : 2016 Building Energy Benchmarking - Ville de Seattle
- **Taille** : 3,376 bâtiments, 46 caractéristiques
- **Période** : Données collectées en 2016
- **Scope** : Bâtiments non résidentiels uniquement

### Caractéristiques principales
- Identifiants et localisation (adresse, quartier, coordonnées GPS)
- Informations structurelles (type, surface, nombre d'étages, année de construction)
- Types d'usage (usage principal, secondaire, tertiaire)
- Métriques énergétiques (électricité, gaz naturel, vapeur)
- Variables cibles : Émissions totales de GES, intensité des émissions

## 🛠️ Installation

### Prérequis
- Python 3.11+
- pip

### Configuration de l'environnement

```bash
# Cloner le repository
git clone https://github.com/Hadri2T/OpenClassroom_projet_3.git
cd Projet_3

# Créer un environnement virtuel (recommandé)
python -m venv venv
source venv/bin/activate  # Sur Windows: venv\Scripts\activate

# Installer les dépendances
pip install -r requirements.txt
```

## 🚀 Usage

Lancer Jupyter Notebook :

```bash
jupyter notebook
```

Puis ouvrir le fichier `P3_template_modelistation_supervisee_data_scientist.ipynb`

## 📁 Structure du Projet

```
Projet_3/
├── .gitignore                          # Fichiers à ignorer par Git
├── requirements.txt                    # Dépendances Python
├── README.md                           # Documentation du projet
├── CLAUDE.md                           # Contexte pour Claude Code
├── 2016_Building_Energy_Benchmarking.csv  # Dataset principal
└── P3_template_modelistation_supervisee_data_scientist.ipynb  # Notebook de travail
```

## 📈 Progression

### ✅ Complété
- [x] Configuration de l'environnement virtuel
- [x] Analyse exploratoire des données
  - [x] Inspection des données et valeurs manquantes
  - [x] Identification des outliers (32 identifiés)
  - [x] Catégorisation des bâtiments
  - [x] Filtrage des bâtiments résidentiels (1,668 bâtiments retenus)
  - [x] Nettoyage des colonnes peu pertinentes

### 🔄 En cours
- [ ] Feature Engineering
- [ ] Comparaison de modèles (DummyRegressor, LinearRegression, SVR, RandomForest)
- [ ] Optimisation du modèle (GridSearchCV)
- [ ] Analyse de l'importance des features

## 🔑 Résultats Clés de l'EDA

- **Types de bâtiments** : 8 catégories identifiées (NonResidential, Multifamily variants, Campus, SPS-District K-12, etc.)
- **Bâtiments multi-usages** : 1,679 bâtiments (49.7%) avec plusieurs usages
- **Outliers** : 32 bâtiments identifiés (23 "Low outlier", 9 "High outlier")
- **Dataset final** : 1,668 bâtiments non résidentiels après filtrage

## 🎓 Livrables Attendus

- Notebook complété avec :
  - Analyse exploratoire documentée
  - Feature engineering avec justification des choix
  - Comparaison de plusieurs modèles supervisés
  - Optimisation du meilleur modèle (GridSearchCV sur 3+ hyperparamètres)
  - Analyse de l'importance des features
- Métriques de performance : R², MAE, RMSE (train et test)

## ⚠️ Points d'Attention

- **Data leakage** : Ne pas utiliser les valeurs de consommation énergétique comme features (seulement l'existence de sources d'énergie)
- **Valeurs manquantes** : Ne pas supprimer toutes les lignes avec des NaN (perte de données)
- **Performance du modèle** : L'objectif est d'apprendre le feature engineering, pas d'optimiser à 100% la performance

## 👤 Auteur

Hadrien - Formation OpenClassrooms Data Scientist

## 📝 Licence

Projet éducatif - OpenClassrooms

## 🔗 Liens Utiles

- [Repository GitHub](https://github.com/Hadri2T/OpenClassroom_projet_3)
- [Seattle Building Energy Benchmarking Data](https://data.seattle.gov/dataset/2016-Building-Energy-Benchmarking/2bpz-gwpy)
