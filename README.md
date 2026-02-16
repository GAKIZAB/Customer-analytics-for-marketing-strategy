# Segmentation Client pour Marketing Ciblé

### *Projet Data Analytics – Clustering & Recommandations Marketing*


## 🧠 Contexte & Objectif

Dans un contexte de marketing data-driven, les entreprises doivent mieux comprendre leurs clients pour personnaliser leurs actions marketing et maximiser leur retour sur investissement.

L’objectif de ce projet est de **segmenter une base clients** d’une entreprise de distribution alimentaire afin de :

* identifier des **profils clients homogènes**,
* comprendre leurs **comportements d’achat**,
* proposer des **recommandations marketing actionnables**.

Ce projet illustre une démarche complète de **Data Analysis appliquée au business**, depuis la préparation des données jusqu’à l’interprétation métier.

## 📦 Données

* 2 240 clients
* Données démographiques : âge, revenu, situation familiale
* Données comportementales : dépenses, fréquence d’achat, canaux utilisés (web, catalogue, magasin)

## 🔍 Démarche analytique

### 1️⃣ Préparation et nettoyage des données

* Suppression des valeurs aberrantes
* Gestion des variables numériques
* Création de variables agrégées (dépenses totales, nombre total d’achats)
* Vérification de la cohérence des données

### 2️⃣ Sélection des variables

10 variables clés ont été retenues pour représenter les dimensions essentielles du comportement client :

| Dimension       | Variables                                                     |
| --------------- | ------------------------------------------------------------- |
| Pouvoir d’achat | `Income`, `Total_Spent`                                       |
| Démographie     | `Age`, `Total_Children`                                       |
| Canaux d’achat  | `NumWebPurchases`, `NumCatalogPurchases`, `NumStorePurchases` |
| Engagement      | `NumWebVisitsMonth`, `Recency`                                |
| Fréquence       | `Total_Purchases`                                             |


### 3️⃣ Standardisation

Les variables ont été **standardisées (z-score)** afin de garantir un poids équivalent dans le modèle de clustering.

## Modélisation – Clustering

### Choix de l’algorithme : **K-Means**

Le clustering **K-Means** a été retenu pour :

* sa **rapidité** sur des jeux de données de taille moyenne,
* son **interprétabilité**,
* sa pertinence pour des **variables numériques continues**.

Des alternatives (clustering hiérarchique) ont été testées mais écartées pour des raisons de lisibilité et de scalabilité.

### Choix du nombre de clusters

* Méthode du coude (inertie)
* Score silhouette
* Analyse métier des segments

➡️ Le choix k = 3 permet un bon compromis entre performance statistique et interprétabilité business.

### Réduction dimensionnelle (PCA)

Une Analyse en Composantes Principales (PCA) a été utilisée pour :

* visualiser les clusters,
* comprendre les axes de différenciation.

➡️ Les 3 premières composantes expliquent 70,1 % de la variance totale.

## 📊 Résultats

### Synthèse des clusters

| Cluster | Profil                | Caractéristiques principales                               |
| ------- | --------------------- | ---------------------------------------------------------- |
| 0       | Budgétaires Familiaux | Revenu faible, familles, faible dépense, achats en magasin |
| 1       | Aisés Connaisseurs    | Revenu élevé, forte dépense, omnicanal, premium            |
| 2       | Connectés             | Revenu intermédiaire, digital, engagés                     |

## 🧩 Interprétation métier

* **Cluster 0** : clients sensibles au prix, nécessitant des stratégies de fidélisation et de volume
* **Cluster 1** : clients à très forte valeur, orientés qualité et expérience
* **Cluster 2** : clients digitaux, à fort potentiel de montée en gamme

## 💡 Recommandations marketing

Pour chaque segment, des **actions marketing ciblées** ont été proposées :

* choix des canaux de communication,
* messages adaptés,
* offres commerciales personnalisées.

👉 L’objectif est de **transformer l’analyse data en décisions opérationnelles**.

## 📈 Impact attendu

* Amélioration de la **personnalisation des campagnes**
* Augmentation estimée du **chiffre d’affaires : +25 %**
* **ROI marketing estimé : x3,5**

## 🛠️ Compétences & Technologies mobilisées

### Data & Analyse

* Python (pandas, numpy)
* Nettoyage et préparation des données
* Feature engineering

### Machine Learning

* Clustering (K-Means)
* Évaluation des modèles (inertie, silhouette)
* Réduction dimensionnelle (PCA)

### Data Visualization

* matplotlib
* seaborn

### Business & Communication

* Interprétation métier des résultats
* Recommandations stratégiques
* Data storytelling

---

## Structure du projet

```text
├── data/
│   ├── marketing_data_raw.csv
│   └── data_cleaned.csv
├── notebooks/
│   ├── 01_exploration_donnees.ipynb
│   ├── 02_analyse_clustering.ipynb
│   └── customer_segmentation_marketing_analysis.ipynb
├── requirements.txt
└── README.md
```

---

## 👤 Auteur

**Bertrand Gakiza**
Data Analyst / Data Scientist
