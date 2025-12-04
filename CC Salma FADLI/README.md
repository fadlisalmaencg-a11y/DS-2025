# 🧬 Clustering sur le Insurance Charges Dataset  
Projet réalisé par Salma Fadli  

## 📁 1. Description du projet  
Ce projet applique différentes méthodes de **clustering** sur le dataset *Insurance Charges*, qui contient des informations sur des individus (âge, sexe, IMC, tabagisme…) ainsi que leurs **frais d’assurance santé**.  

L’objectif est de :  
- Nettoyer et préparer les données  
- Explorer les variables et comprendre leurs relations  
- Appliquer plusieurs algorithmes de clustering  
- Comparer les performances et interpréter les groupes obtenus  

Dataset utilisé :  
Fournit sur Kaggle dans le notebook suivant :  
> *Clustering Insurance Charges Dataset* (Yousef Eddin)

## 📁 2. Résultat des analyses effectuées
🔹 1. Prétraitement

Chargement du dataset

Vérification des valeurs manquantes

Encodage des variables catégorielles

Normalisation des variables numériques

🔹 2. Analyse exploratoire (EDA)

Distribution de l'âge, du BMI et des charges

Comparaison fumeurs vs non fumeurs

Heatmap des corrélations

Visualisation 2D & 3D des points

🔹 3. Méthodes de clustering testées

K-Means (méthode du coude pour trouver K optimal)

Agglomerative Clustering

DBSCAN

Comparaison par silhouette score

🔹 4. Résultats principaux

Le clustering K-Means avec k = 3 donne les groupes les plus cohérents

Les principaux facteurs expliquant les clusters sont :

Tabagisme (variable la plus discriminante)

BMI

Charges

Les fumeurs forment un groupe séparé avec des coûts très élevés

Les non fumeurs se séparent en deux groupes selon l’IMC

## 📁3. Résumé des analyses effectuées

Le clustering appliqué au dataset d’assurance santé montre clairement que :

Les fumeurs constituent un groupe séparé en raison de charges très élevées

Les non fumeurs se divisent selon leur IMC

Le modèle K-Means (k=3) donne la séparation la plus interprétable

Ce projet fournit une analyse claire et reproductible, idéale pour un devoir de data science ou un rapport académique.---

## ⚙️ 4. Installation & Pré-requis  

Aucune installation avancée n’est requise, seulement les librairies classiques de Python :

```python
pip install numpy pandas matplotlib seaborn scikit-learn
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

# --- 1. Charger la BDD directement depuis GitHub ---
url = "https://raw.githubusercontent.com/stedy/Machine-Learning-with-R-datasets/master/insurance.csv"
df = pd.read_csv(url)

# --- 2. Encodage ---
df_enc = df.copy()
df_enc["sex"] = df_enc["sex"].map({"male":0, "female":1})
df_enc["smoker"] = df_enc["smoker"].map({"no":0, "yes":1})
df_enc = pd.get_dummies(df_enc, columns=["region"], drop_first=True)

# --- 3. Normalisation ---
scaler = StandardScaler()
X = scaler.fit_transform(df_enc)

# --- 4. K-Means ---
inertia = []
for k in range(2,8):
    km = KMeans(n_clusters=k, random_state=42)
    km.fit(X)
    inertia.append(km.inertia_)

plt.plot(range(2,8), inertia, marker='o')
plt.title("Méthode du coude")
plt.xlabel("Nombre de clusters")
plt.ylabel("Inertia")
plt.show()

# K optimal = 3
kmeans = KMeans(n_clusters=3, random_state=42)
labels = kmeans.fit_predict(X)
df["cluster"] = labels

# --- 5. Résultats ---
print(df.groupby("cluster").mean())

sns.scatterplot(x=df['bmi'], y=df['charges'], hue=df['cluster'], palette="Set1")
plt.title("Clusters sur BMI vs Charges")
plt.show()

