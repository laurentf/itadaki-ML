# 🍽️ Prédiction du Niveau Calorique des Recettes

## 📋 Description du Projet

Ce projet utilise l'intelligence artificielle pour **prédire automatiquement le niveau calorique des recettes** à partir de leur liste d'ingrédients.

### 🎯 Objectif

Classifier les recettes en **3 niveaux caloriques** :

- 🟢 **BAS** : moins de 300 calories
- 🟡 **MOYEN** : 300 à 600 calories
- 🔴 **HAUT** : plus de 600 calories

### 💡 Pourquoi c'est utile ?

- ✅ **Évaluation rapide** d'une nouvelle recette
- ✅ **Aide à la planification** de repas équilibrés
- ✅ **Compréhension** des ingrédients qui influencent les calories
- ✅ **Automatisation** de l'analyse nutritionnelle

## 🧠 Techniques Utilisées

### Machine Learning

- **Random Forest** avec optimisation des hyperparamètres
- **Gestion du déséquilibre** des classes (sous-échantillonnage)
- **Validation croisée** pour évaluer les performances

### Traitement du Langage Naturel (NLP)

- **Nettoyage avancé** des ingrédients (suppression quantités, préparations)
- **Vectorisation TF-IDF** pour transformer le texte en données numériques
- **Focus sur les ingrédients** (plus prédictifs que les instructions)

### Interprétabilité

- **Analyse SHAP** pour comprendre les prédictions
- **Importance des features** pour identifier les ingrédients clés
- **Visualisations** des résultats

## 📊 Dataset

- **Source** : https://www.kaggle.com/datasets/shuyangli94/food-com-recipes-and-user-interactions?select=PP_users.csv => `data/RAW_recipes.csv` (~230K recettes)
- **Colonnes utilisées** : `ingredients`, `nutrition`, `name`
- **Preprocessing** : Extraction des calories, nettoyage NLP, équilibrage

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

## 📈 Performances Attendues

- **Accuracy** : ~85-90% sur le jeu de test
- **Temps d'entraînement** : 8-12 minutes
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
├── calorie_prediction_notebook.ipynb  # Notebook principal
├── data/
│   └── RAW_recipes.csv                # Dataset des recettes
├── requirements.txt                   # Dépendances Python
├── README.md                         # Ce fichier
└── itadaki_venv/                     # Environnement virtuel
```

## 🔧 Fonctionnalités Avancées

### Preprocessing Intelligent

- **Suppression automatique** des quantités (1 cup, 2 tbsp, etc.)
- **Nettoyage des préparations** (chopped, diced, minced, etc.)
- **Normalisation alphabétique** pour cohérence des prédictions
- **Stop words culinaires** spécialisés

### Gestion du Déséquilibre

- **Sous-échantillonnage** à 60K échantillons par classe
- **Poids de classes équilibrés** dans Random Forest
- **Stratification** lors de la division train/test

### Interprétabilité

- **SHAP values** pour expliquer chaque prédiction
- **Feature importance** pour identifier les mots-clés importants
- **Visualisations** des patterns découverts

## 📚 Technologies

- **Python 3.12+**
- **Pandas** - Manipulation des données
- **Scikit-learn** - Machine Learning
- **NLTK** - Traitement du langage naturel
- **SHAP** - Interprétation des modèles
- **Matplotlib/Seaborn** - Visualisations

## ⚡ Optimisations

### Performances

- **Équilibrage intelligent** des classes
- **TF-IDF optimisé** pour les ingrédients culinaires
- **Grid Search** avec paramètres adaptés
- **Parallélisation** sur tous les cœurs CPU

### Temps d'Exécution

- **Dataset équilibré** : 60K échantillons par classe
- **Features réduites** : Focus sur les ingrédients essentiels
- **Hyperparamètres pré-optimisés**

## 🎯 Cas d'Usage

1. **Développeurs d'apps culinaires** : Intégration de l'évaluation calorique
2. **Nutritionnistes** : Aide à l'analyse rapide des recettes
3. **Particuliers** : Évaluation de nouvelles recettes
4. **Chercheurs** : Analyse des patterns alimentaires

## 🔮 Améliorations Futures

- **Prédiction des calories exactes** (régression)
- **Classification multi-nutriments** (protéines, lipides, glucides)
- **Intégration d'images** de plats
- **API REST** pour utilisation en production
- **Interface web** interactive

## 📞 Support

Pour toute question ou suggestion :

- Consultez le notebook avec ses explications détaillées
- Vérifiez les commentaires dans le code
- Testez avec vos propres recettes !

## 🏆 Résultats

Ce projet démontre qu'il est possible de **prédire efficacement le niveau calorique** d'une recette en analysant uniquement sa liste d'ingrédients, avec une précision de ~85-90%.

Les **ingrédients les plus prédictifs** identifiés :

- **Calories élevées** : butter, cream, sugar, chocolate, nuts, cheese
- **Calories modérées** : chicken, rice, oil, bread, pasta
- **Calories faibles** : vegetables, herbs, spices, broth, vinegar

---

_Projet développé dans le cadre de l'apprentissage du Machine Learning appliqué à la nutrition._
