# Analyse et Clustering des Alliages Métalliques Amorphes

## 📘 Description du Projet

Ce projet traite d’un ensemble de données sur des alliages métalliques amorphes (BMGs) extraites du fichier `BMGs-2024.odt`, converti en Excel pour faciliter l’analyse. L'objectif est de nettoyer, transformer, analyser et regrouper les compositions chimiques d’alliages pour en extraire des connaissances exploitables à l’aide d’outils Python et de méthodes de clustering.

---

## 🔍 Chapitre 1 – Traitement des Données des Alliages

### 1.1 Introduction
- Conversion du fichier OpenDocument en Excel.
- Objectif : nettoyer et structurer les données pour l’analyse.

### 1.2 Lecture et Fusion des Tableaux
- Deux tableaux extraits (`df1`, `df2`) du fichier Excel `BMGs-2024.xlsx`.
- Suppression des lignes vides et renommage des colonnes.
- Fusion des tableaux pour obtenir un `DataFrame` unique (`df_combined`).

### 1.3 Nettoyage Initial
- Nettoyage de la colonne `Alloys` : suppression des espaces superflus tout en conservant la structure des groupes (accolades, crochets, parenthèses).

### 1.4 Traitement Avancé des Compositions
- Calcul des pourcentages selon la priorité des groupes : `{}` > `[]` > `()`.
- Exemple traité : `{[(Fe60Co40)75B20Si5]96Nb4}97Cr3`  
  ➤ Résultat : `Fe=41.9`, `Co=27.9`, `B=18.6`, `Si=4.6`, `Nb=3.88`, `Cr=3`.

### 1.5 Analyse des Formules Incorrectes
- Validation des formules chimiques avec expressions régulières.
- Exemple de formules erronées :
  - `Fe58MoB111:L14514C15B6Cr5Er2` (caractère “:”, quantités anormales)
  - `Ti0.45 Cu0.378 Zr0.1 Ni0.072 Sn` (élément sans quantité)

### 1.6 Structuration des Données
- Extraction des éléments chimiques et quantités dans des colonnes distinctes.
- Résultat : format tabulaire facilitant l’analyse quantitative.

### 1.7 Validation Chimique
- Vérification que les éléments extraits figurent bien dans la table périodique.
- Éléments non valides détectés : `L`, `Mm`.

### 1.8 Vérification des Pourcentages
- Somme des pourcentages pour chaque formule : attendue dans [99.5%, 100.5%].
- Aucune anomalie détectée.

---

## 🤖 Chapitre 2 – Clustering des Alliages

### 2.1 Objectif
- Segmenter les alliages en groupes homogènes selon leurs compositions chimiques.

### 2.2 Méthodologie
1. **Détermination du nombre de clusters :**  
   ➤ Méthode du coude → nombre optimal : `k = 4`.

2. **Application de l’algorithme KMeans :**  
   ➤ Clustering effectué, colonne `Cluster` ajoutée.

3. **Réduction de dimensionnalité avec PCA :**  
   ➤ Visualisation 2D des clusters.

### 2.3 Analyse Post-Clustering
- Moyennes des pourcentages par élément et par cluster.
- Exemples :
  - Le Fer (`Fe`) est dominant dans le cluster 2.
  - Le Cuivre (`Cu`) et le Zirconium (`Zr`) varient selon les groupes.

### 2.4 Évaluation
- Score de Silhouette : **`0.411`**  
  ➤ Indique une séparation modérément bonne des clusters.

### 2.5 Propriétés Physiques par Cluster
- Moyenne de `Tg`, `Tx`, `Tl`, `Dmax` par groupe.
- Exemple :
  - Cluster 2 : `Tg = 685.21`, `Dmax = 7.55` → meilleure formabilité.

---

## 🛠️ Technologies Utilisées

- **Python**
- **Pandas / NumPy**
- **Scikit-learn** (KMeans, PCA, silhouette_score)
- **Matplotlib / Seaborn** (visualisation)
- **Regex** pour le parsing des formules chimiques
- **Jupyter Notebook** pour l’analyse interactive

---


---

## 📌 Résumé des Résultats

- Données d’alliages correctement nettoyées, structurées et validées.
- Groupes d’alliages identifiés par similitude de composition.
- Clustering cohérent avec un score de silhouette de 0.411.
- Possibilités d’optimisation des matériaux via analyse comparative des clusters.

---

## 📈 Pistes d’Amélioration

- Intégrer des propriétés mécaniques supplémentaires (densité, module, etc.).
- Appliquer d'autres algorithmes de clustering (DBSCAN, Agglomerative).
- Étendre l'analyse à de nouvelles bases de données de matériaux.

---

## 👨‍🔬 Auteur

Projet réalisé dans le cadre d’une étude sur les alliages métalliques amorphes.

---

