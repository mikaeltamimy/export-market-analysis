# 🌍 Analyse de Marchés à l’Export — Secteur Agroalimentaire

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4B8BBE?style=for-the-badge&logo=python&logoColor=white)

> Identification des pays cibles pour l’exportation de **viande de volaille** via l’analyse de données économiques et commerciales internationales (FAO / Banque Mondiale).

-----

## 🎯 Objectif

Aider une entreprise agroalimentaire à **identifier les marchés les plus attractifs** à l’international, en segmentant les pays selon leur dépendance aux importations, leur croissance démographique et leur PIB.

-----

## 📦 Données utilisées

|Dataset                             |Source         |Période  |
|------------------------------------|---------------|---------|
|Population par pays                 |FAO            |2000–2018|
|Disponibilité alimentaire (volaille)|FAO            |2017     |
|PIB par pays                        |Banque Mondiale|2017     |

-----

## 🔄 Pipeline du projet

```
Import & Nettoyage → Feature Engineering → Jointures → Clustering → ACP → Recommandations
```

### 1. 🧹 Prétraitement

- Nettoyage des valeurs manquantes (PIB, population)
- Calcul du **taux de croissance démographique** (2012–2017)
- Détection et traitement des outliers (boxplots + IQR)

### 2. ⚙️ Feature Engineering

- **TDI** — Taux de Dépendance aux Importations = (Importations / Disponibilité intérieure) × 100
- **TAS** — Taux d’Auto-Suffisance = (Production / Disponibilité intérieure) × 100
- Jointure de 3 datasets sur la variable `Zone` (pays)

### 3. 🤖 Modélisation

|Méthode                          |Usage                                   |
|---------------------------------|----------------------------------------|
|**K-Means**                      |Segmentation des pays en clusters       |
|**CAH** (Clustering Hiérarchique)|Validation de la segmentation           |
|**ACP** (PCA)                    |Réduction dimensionnelle & visualisation|

### 4. 🎯 Résultats

- **5 composantes principales** retenues (critère de Kaiser)
- **F1** représente les disponibilités alimentaires
- **F2** oppose TDI élevé vs TAS élevé
- **Cluster cible identifié** : pays à fort TDI, faible TAS, PIB élevé → forte dépendance aux importations de volaille

-----

## 🗺️ Pays cibles recommandés

Les pays sélectionnés présentent :

- ✅ Taux de dépendance aux importations **élevé**
- ✅ Taux d’auto-suffisance **faible**
- ✅ PIB et disponibilités alimentaires **élevés**
- ✅ Croissance démographique **positive**

-----

## 🛠️ Stack technique

|Librairie               |Usage                                                 |
|------------------------|------------------------------------------------------|
|`pandas` / `numpy`      |Manipulation & feature engineering                    |
|`scikit-learn`          |K-Means, PCA, normalisation                           |
|`scipy`                 |Clustering hiérarchique (CAH)                         |
|`matplotlib` / `seaborn`|Visualisations (dendrogramme, cercle des corrélations)|
|`kneed` / `yellowbrick` |Détermination du nombre optimal de clusters           |

-----

## 📁 Structure du projet

```
export-market-analysis/
│
├── Produisez_une_etude_de_marche.ipynb   # Notebook principal
├── Population_2000_2018.csv               # Données population
├── DisponibiliteAlimentaire_2017.csv      # Données FAO
├── Pib_2017.csv                           # Données PIB
└── README.md
```

-----

## 👤 Auteur

**Mikaël Tamimy** — Data Analyst
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Mika%C3%ABl%20Tamimy-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/mikael-tamimy-56b144182)
