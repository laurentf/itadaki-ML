# 🍽️ Prédiction du niveau calorique des Recettes

## 📋 Description du projet

Ce projet utilise l'intelligence artificielle pour **prédire automatiquement le niveau calorique des recettes** à partir de leur liste d'ingrédients avec un preprocessing NLP avancé et un thème visuel harmonisé.

### 🎯 Objectif

Classifier les recettes en **3 niveaux caloriques** :

- 🟢 **BAS** : moins de 250 calories
- 🟡 **MOYEN** : 250 à 500 calories
- 🔴 **HAUT** : plus de 500 calories

### 💡 Pourquoi c'est utile ?

- ✅ **Évaluation rapide** d'une nouvelle recette
- ✅ **Aide à la planification** de repas équilibrés
- ✅ **Compréhension** des ingrédients qui influencent les calories
- ✅ **Automatisation** de l'analyse nutritionnelle

## 🧠 Techniques Utilisées

### Machine Learning

- **Random Forest** avec optimisation des hyperparamètres
- **LabelEncoder** pour une gestion correcte des classes et ordre logique
- **Gestion du déséquilibre** avec `class_weight='balanced'`
- **Validation croisée** pour évaluer les performances

### Traitement du Langage Naturel (NLP) Avancé

- **NLTK** pour lemmatisation et tokenisation professionnelle
- **Stop words culinaires personnalisés** (75+ termes spécialisés)
- **Nettoyage intelligent** des quantités et préparations
- **Tri alphabétique** des ingrédients pour cohérence
- **Vectorisation TF-IDF** optimisée pour les ingrédients culinaires

### Explicabilité et Visualisation

- **Analyse SHAP** pour comprendre les prédictions
- **Thème visuel sombre harmonisé** avec palette de couleurs professionnelle
- **Visualisations interactives** des prédictions avec graphiques 4-panels
- **Feature importance** pour identifier les ingrédients clés

## 📊 Dataset

- **Source** : https://www.kaggle.com/datasets/shuyangli94/food-com-recipes-and-user-interactions?select=PP_users.csv => à mettre dans `data/RAW_recipes.csv` (~230K recettes)
- **Colonnes utilisées** : `ingredients`, `nutrition`, `name`
- **Preprocessing** : Extraction des calories, nettoyage NLP avancé, équilibrage
- **Distribution finale** : bas (39.7%), moyen (34.7%), haut (25.7%)

## 🚀 Installation et Utilisation

### 1. Prérequis

```bash
# Créer l'environnement virtuel
python -m venv itadaki_venv

# Activer l'environnement (Windows)
.\itadaki_venv\Scripts\Activate.ps1

# Installer les dépendances
pip install -r requirements.txt
```

### 2. Lancement du Notebook

```bash
# Démarrer Jupyter
jupyter notebook calorie_prediction_notebook.ipynb
```

### 3. Utilisation du Modèle

```python
# Exemple de prédiction
ingredients = "butter, heavy cream, sugar, eggs, chocolate, flour"
prediction, probabilities = predict_calorie_level(ingredients)

print(f"Niveau calorique prédit : {prediction}")
print(f"Probabilités : {probabilities}")
```

## 📈 Performances

### ⚠️ État Actuel du Modèle

- **Accuracy de validation croisée** : ~51% (en cours d'optimisation)
- **Problème identifié** : GridSearch avec paramètres trop restrictifs
- **Solution en cours** : Optimisation des hyperparamètres Random Forest

### 🎯 Performances Cibles (après optimisation)

- **Accuracy attendue** : 65-75% sur le jeu de test
- **Temps d'entraînement** : 15-20 minutes avec paramètres optimisés
- **Prédiction** : Instantanée

### Exemples de Prédictions

| Ingrédients                             | Prédiction | Justification                                   |
| --------------------------------------- | ---------- | ----------------------------------------------- |
| `spinach, tomatoes, garlic, herbs`      | 🟢 BAS     | Légumes faibles en calories                     |
| `chicken, rice, vegetables, olive oil`  | 🟡 MOYEN   | Protéine + glucides + matières grasses modérées |
| `butter, cream, sugar, chocolate, nuts` | 🔴 HAUT    | Ingrédients riches en calories                  |

## 📁 Structure du Projet

```
itadaki_ML/
├── calorie_prediction_notebook.ipynb  # Notebook principal avec thème sombre
├── data/
│   └── RAW_recipes.csv                # Dataset des recettes
├── requirements.txt                   # Dépendances Python (+ NLTK)
├── README.md                         # Ce fichier
└── itadaki_venv/                     # Environnement virtuel
```

## 🔧 Fonctionnalités Avancées

### Preprocessing NLP Intelligent

- **NLTK lemmatisation** pour normaliser les mots (cooking → cook)
- **Tokenisation professionnelle** avec gestion des cas spéciaux
- **Stop words culinaires** : chopped, diced, cup, tbsp, large, small, etc.
- **Suppression des quantités** et unités de mesure
- **Tri alphabétique** des ingrédients pour cohérence des prédictions

### Gestion du Déséquilibre

- **LabelEncoder** avec ordre logique garanti (bas=0, moyen=1, haut=2)
- **class_weight='balanced'** pour équilibrer automatiquement
- **Stratification** lors de la division train/test

### Interface Visuelle Harmonisée

- **Thème sombre professionnel** avec palette de 10 couleurs
- **Graphiques 4-panels** pour analyse complète des prédictions
- **Matrices de confusion** avec style personnalisé
- **Plots SHAP** adaptés au thème sombre

## 📚 Technologies

- **Python 3.12+**
- **Pandas** - Manipulation des données
- **Scikit-learn** - Machine Learning et LabelEncoder
- **NLTK** - Traitement avancé du langage naturel
- **SHAP** - Interprétation des modèles
- **Matplotlib/Seaborn** - Visualisations avec thème personnalisé

## ⚡ Optimisations

### Performances

- **LabelEncoder** pour gestion optimale des classes
- **TF-IDF optimisé** avec paramètres adaptés aux ingrédients
- **class_weight='balanced'** pour gérer le déséquilibre
- **Parallélisation** sur tous les cœurs CPU

### Temps d'Exécution

- **Preprocessing NLTK optimisé** avec cache des ressources
- **GridSearch configuré** pour équilibre performance/temps
- **Features TF-IDF** limitées à 5000 pour efficacité

## 🔮 Améliorations Futures

- **Optimisation des hyperparamètres** Random Forest (en cours)
- **Prédiction des calories exactes** (régression)
- **Classification multi-nutriments** (protéines, lipides, glucides)
- **Intégration d'images** de plats
- **API REST** pour utilisation en production

## 📞 Support

Pour toute question ou suggestion :

- Consultez le notebook avec ses explications détaillées
- Vérifiez les commentaires dans le code
- Testez avec vos propres recettes !

## 🏆 Résultats

Ce projet démontre l'utilisation de **techniques NLP avancées** pour la prédiction du niveau calorique des recettes, avec un **preprocessing intelligent** et une **interface visuelle professionnelle**.

Les **ingrédients les plus prédictifs** identifiés par le modèle :

- **Calories élevées** : butter, cream, sugar, chocolate, nuts, cheese
- **Calories modérées** : chicken, rice, oil, bread, pasta
- **Calories faibles** : vegetables, herbs, spices, broth, vinegar

### 🎨 Interface Visuelle

Le projet inclut un **thème sombre harmonisé** avec :

- Palette de couleurs professionnelle (10 couleurs)
- Visualisations interactives des prédictions
- Graphiques SHAP adaptés au thème sombre
- Interface 4-panels pour analyse complète

---

_Projet développé dans le cadre de l'apprentissage du Machine Learning et de la soutenance certification bloc C3 (formation Alyra)._
