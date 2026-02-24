# Segmentation Client pour Campagnes Marketing (Projet Data Mining)

## 1. Objectif du Projet

L'objectif principal de ce projet est de réaliser une segmentation précise de la clientèle d'une entreprise afin de mieux comprendre ses différents profils d'acheteurs. En utilisant des techniques de clustering, nous visons à identifier des groupes de clients homogènes en fonction de leurs caractéristiques démographiques (âge, revenus) et de leur comportement d'achat (dépenses par catégorie de produits, canaux d'achat utilisés).

Cette segmentation permettra à l'entreprise de :
- Mieux cibler ses actions marketing en adaptant les offres et les messages à chaque segment.
- Comprendre les préférences de chaque groupe (produits favoris, canaux d'achat privilégiés).
- Optimiser ses stratégies de fidélisation et de développement de chiffre d'affaires.

## 2. Méthodologie et Justification des Choix

Le projet s'est déroulé en deux phases principales, détaillées dans les notebooks `01_exploration_donnees.ipynb` et `02_analyse_clustering.ipynb`.

### a) Exploration et Préparation des Données

Avant toute modélisation, une exploration approfondie des données a été menée :
- **Nettoyage** : Gestion des valeurs manquantes sur la variable `Income`.
- **Feature Engineering** : Création de nouvelles variables plus pertinentes pour la segmentation, telles que :
    - `Total_Children` : nombre total d'enfants.
    - `Total_Purchases` : nombre total d'achats.
    - `Avg_Basket` : panier moyen.
    - `Income_Category` : catégorisation des revenus (Faible, Moyen, Élevé, Très élevé).
- **Sélection des Variables** : Pour le clustering, nous avons sélectionné un ensemble de 10 variables numériques clés, incluant le revenu, l'âge, les dépenses totales, le nombre d'achats par canal, etc.
- **Standardisation** : Les données ont été standardisées à l'aide de `StandardScaler`. Cette étape est **cruciale** pour le clustering, car elle permet de donner le même poids à toutes les variables, évitant que celles avec des échelles plus grandes (comme le revenu) ne dominent le résultat.

### b) Segmentation par Clustering (K-Means)

La méthode de clustering retenue est **K-Means**. Ce choix se justifie pour les raisons suivantes :
- **Efficacité** : K-Means est un algorithme rapide et efficace, adapté aux volumes de données de taille moyenne.
- **Interprétabilité** : Les résultats sont faciles à interpréter. Chaque client se voit attribuer un cluster, et chaque cluster est caractérisé par son centre (le "profil moyen").
- **Objectif du projet** : L'objectif est de créer des groupes d'achats distincts et bien séparés, ce que K-Means cherche à optimiser.

Pour déterminer le nombre optimal de clusters (`k`), nous avons utilisé deux méthodes :
1.  **La Méthode du Coude (Elbow Method)** : En analysant le graphique de l'inertie (somme des distances intra-cluster) en fonction de `k`, on cherche le point où la courbe s'infléchit.
2.  **Le Score de Silhouette** : Cette métrique évalue la cohésion interne des clusters et leur séparation. Un score proche de 1 indique des clusters bien distincts. Le meilleur score a été obtenu pour `k=2`, mais nous avons retenu `k=3` pour un équilibre entre la qualité statistique et la richesse de l'interprétation métier.

## 3. Résultats Obtenus

L'application du K-Means avec 3 clusters a permis d'identifier trois segments de clientèle distincts. Les profils moyens de ces segments sont résumés ci-dessous :

| Caractéristique | **Cluster 0** | **Cluster 1** | **Cluster 2** |
| :--- | :--- | :--- | :--- |
| **Taille** | 1047 clients (47.2%) | 520 clients (23.5%) | 649 clients (29.3%) |
| **Revenu** | Faible (35k€) | Très élevé (78k€) | Élevé (59k€) |
| **Âge** | 53 ans | 56 ans | 58 ans |
| **Dépenses totales** | Très faibles (101€) | Très élevées (1398€) | Élevées (790€) |
| **Achats Web / Catalogue / Magasin** | 2.1 / 0.6 / 3.2 | 4.8 / 6.4 / 8.4 | 6.7 / 3.0 / 7.9 |
| **Produits favoris** | (Dépenses très faibles) | Vins, Viandes | Vins, Or |
| **Présence d'enfants** | Oui | Non | Oui |

## 4. Interprétation des Résultats

L'analyse des profils moyens permet de qualifier chaque segment :

- **Cluster 0 - "Les Petits Budgets" (47.2%)** : Ce segment est le plus large. Il est composé de clients avec des revenus et des dépenses très faibles. Ils ont tendance à acheter principalement en magasin. Ce groupe est probablement sensible au prix et nécessite des offres promotionnelles pour être activé.

- **Cluster 1 - "Les Gros Dépensiers" (23.5%)** : C'est le segment le plus précieux. Ces clients ont des revenus très élevés et dépensent massivement. Ils sont très actifs sur tous les canaux, avec une préférence marquée pour le catalogue et le magasin. Ils ne semblent pas avoir d'enfants. Les stratégies de fidélisation haut de gamme (ventes privées, avant-premières) seraient les plus adaptées.

- **Cluster 2 - "Les Acheteurs Connectés Aisés" (29.3%)** : Ce segment a un bon pouvoir d'achat et des dépenses élevées. Il se distingue par sa préférence pour le canal web (le plus haut score) et les achats en magasin. Les produits "Or" sont également plus populaires dans ce groupe. Une stratégie omnicanale, avec un fort accent sur le digital, serait pertinente pour ce segment.

En conclusion, ce projet de segmentation a permis de mettre en lumière des différences significatives entre les clients. Les trois profils identifiés offrent une base solide pour le déploiement de stratégies marketing différenciées, visant à augmenter l'efficacité des campagnes et la satisfaction client.