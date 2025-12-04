#Salma FADLI G2 Finance
# Assurance Santé
# 🩺 Medical Cost Personal Dataset — Compte Rendu

## 📌 Description générale
Le **Medical Cost Personal Dataset** est un jeu de données populaire provenant de Kaggle, utilisé pour analyser et prédire les **coûts d’assurance santé** en fonction de caractéristiques démographiques, physiques et comportementales.  
Il constitue une excellente base pour des projets d’analyse de données et de machine learning (régression).

---

## 📊 Objectif du dataset
Ce dataset permet de :

- prédire les coûts d’assurance (`charges`)
- analyser les facteurs influençant les dépenses de santé
- comprendre l’impact du tabagisme, de l’IMC ou de l’âge
- créer des modèles de tarification ou de scoring de risque

---

## 📁 Structure du dataset

| Variable      | Type    | Description |
|---------------|---------|-------------|
| `age`         | int     | Âge du bénéficiaire |
| `sex`         | object  | Sexe (`male`/`female`) |
| `bmi`         | float   | Indice de masse corporelle |
| `children`    | int     | Nombre d'enfants couverts |
| `smoker`      | object  | Statut fumeur (`yes`/`no`) |
| `region`      | object  | Région de résidence |
| `charges`     | float   | Coût d’assurance facturé |

**Taille du dataset** : 1 338 lignes  
**Colonnes** : 7 variables

---

## 🧹 Qualité et intégrité des données
- Aucune valeur manquante
- Données propres et cohérentes
- Quelques valeurs extrêmes logiques (ex : IMC très élevé)
- Prêt pour analyse et modélisation

---

## 🔍 Analyses possibles

### 1. Analyse exploratoire (EDA)
- Étude de la distribution de l’âge, du BMI, de `charges`
- Comparaison fumeurs / non-fumeurs
- Variation des coûts selon les régions
- Visualisation des relations (boxplots, histograms, heatmap)

### 2. Corrélations
Facteurs les plus liés aux coûts :
- tabagisme (`smoker`)
- âge (`age`)
- IMC (`bmi`) — surtout en cas d’obésité
- interaction fumeur × BMI

### 3. Modélisation
Modèles adaptés :
- Régression linéaire
- Random Forest Regressor
- Gradient Boosting / XGBoost
- Réseaux neuronaux simples

---

## 📈 Résultats typiques observés
- Les **fumeurs** ont des coûts **2 à 3 fois supérieurs** aux non-fumeurs.
- Le coût augmente fortement avec l’âge, surtout entre 20 et 50 ans.
- Un IMC élevé génère une hausse notable des charges.
- La région a un impact limité sur les dépenses.

---

## 🔐 Licence
Usage permis pour **projets éducatifs**, data science et exploration.  
Toujours vérifier la licence actuelle sur la page Kaggle du dataset.

---

## 📦 Source
Dataset : *Medical Cost Personal Dataset* — Kaggle.


