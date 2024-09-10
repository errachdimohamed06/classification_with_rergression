# classification_with_rergression

### 4. Pour les listes
Les listes sont formatées avec des tirets (`-`) ou des numéros (`1.`, `2.`, etc.).

### Contenu formaté pour README.md

Voici le contenu final avec quelques parties de code formatées pour que vous puissiez le coller directement dans votre `README.md` :

```markdown
# Analyse et Modélisation d'un Dataset COVID-19

Ce projet a pour but d'explorer, analyser et modéliser un dataset COVID-19 téléchargé depuis Kaggle. L'objectif est de comprendre les données et de développer des modèles prédictifs capables d'identifier les cas positifs de COVID-19 en se basant sur des caractéristiques médicales et biologiques.

## 1. Exploration des Données

### 1.1 Objectif
L'exploration des données permet de :
- Comprendre en profondeur la structure et la composition du dataset.
- Identifier les variables clés et les relations potentiellement importantes.
- Élaborer une stratégie de modélisation préliminaire.

### 1.2 Structure des Données
- **Variable cible :** Le résultat de l'examen SARS-Cov-2, indiquant si un individu est positif ou négatif au COVID-19.
- **Dimensions :** Le dataset contient 5644 observations et 111 variables.
- **Types de variables :** 70 variables sont qualitatives (catégoriques) et 41 sont quantitatives (numériques).

### 1.3 Analyse des Valeurs Manquantes
- Une grande proportion des variables (plus de 90%) contient des valeurs manquantes, ce qui constitue un défi majeur pour la modélisation.
- Les données se divisent en deux grands groupes :
  - **76% des observations** concernent des tests viraux.
  - **89% des observations** concernent des taux sanguins.

## 2. Analyse de Fond

### 2.1 Visualisation de la Variable Cible
- Le dataset révèle que seulement **10%** des individus testés sont positifs au COVID-19, ce qui représente 558 cas positifs sur 5000.

### 2.2 Signification des Variables
- **Variables continues :** Standardisées et asymétriques, principalement liées aux tests sanguins.
- **Âge :** Les données relatives à l'âge sont difficiles à interpréter en raison d'un prétraitement inconnu.
- **Variables qualitatives :** Principalement binaires, liées aux résultats de tests viraux.

### 2.3 Relations Entre Variables et Cible
- **Tests sanguins :** Les taux de Monocytes, Plaquettes et Leucocytes semblent corrélés avec le statut COVID-19, suggérant une piste d'investigation pour la modélisation.
- **Âge :** Les individus jeunes semblent moins affectés, mais cette interprétation est limitée par l'absence de détails sur l'âge exact et la période des données.
- **Co-infections virales :** Les données montrent que les co-infections virales sont rares et n'ont pas de lien direct avec le COVID-19.

### 2.4 Hypothèses
- **Hypothèse nulle (H0) :** Les taux de Leucocytes, Monocytes et Plaquettes ne diffèrent pas significativement entre les individus positifs et négatifs au COVID-19.
- **Alternative :** Les individus atteints de COVID-19 présentent des différences significatives dans ces taux.

## 3. Modélisation Initiale

### 3.1 Modèle Baseline
- **Modèle :** `DecisionTreeClassifier` sans hyperparamètres avancés.
- **Évaluation :** Le modèle a donné un f1-score de 0,27 pour les cas positifs, avec une précision de 88% pour les cas négatifs et de 50% pour les positifs.

### 3.2 Amélioration avec un Pipeline
- **Pipeline :** Combinant `PolynomialFeatures`, `SelectKBest`, et `RandomForestClassifier`.
- **Évaluation :** Une légère amélioration avec un f1-score de 0,40 pour les cas positifs.

## 4. Modélisation Avancée

### 4.1 Comparaison de Modèles
- **Modèles testés :** `RandomForestClassifier`, `AdaBoostClassifier`, `SVC`, et `KNeighborsClassifier`.
- **Meilleur Modèle :** Le modèle SVM (`SVC`) a montré les meilleures performances parmi les quatre modèles testés.

### 4.2 Optimisation des Hyperparamètres
- **Technique :** Utilisation de `GridSearchCV` et `RandomizedSearchCV` pour affiner les hyperparamètres du SVM.
- **Hyperparamètres explorés :**
  - `gamma`, `C`, degré des `PolynomialFeatures`, et nombre de variables sélectionnées avec `SelectKBest`.
- **Résultats :** Après 20 itérations de `RandomizedSearchCV`, le f1-score pour les cas positifs a augmenté de 0,27 à 0,55, montrant une nette amélioration malgré les données fortement incomplètes.

## 5. Conclusion

Malgré les défis posés par un dataset contenant plus de 90% de valeurs manquantes dans certaines colonnes, les techniques avancées de modélisation et d'optimisation ont permis de développer un modèle SVM performant. Ce projet illustre l'importance d'une exploration minutieuse des données et de l'optimisation des hyperparamètres dans le développement de modèles prédictifs robustes.
