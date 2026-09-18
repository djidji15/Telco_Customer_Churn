

Projet de data science  : prédire la résiliation (churn) des clients d'une entreprise de télécommunications à partir de leurs caractéristiques contractuelles, de leurs services souscrits et de leur facturation.

# Telco_Customer_Churn
# Prédiction du Churn Client — Telco Customer Churn

Projet de data science : prédire la résiliation (churn) des clients d'une entreprise de télécommunications à partir de leurs caractéristiques contractuelles, de leurs services souscrits et de leur facturation.
## Dataset

**Telco Customer Churn** (IBM Sample Dataset) — 7 043 clients, 21 colonnes.

| Type | Colonnes |
|---|---|
| Démographie | `gender`, `SeniorCitizen`, `Partner`, `Dependents` |
| Services | `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies` |
| Contrat & facturation | `Contract`, `PaperlessBilling`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`, `tenure` |
| Cible | `Churn` (Yes/No) |

## Structure du projet

```
telco-churn-project/
├── data/
│   └── telco_churn.csv          # dataset brut
├── notebooks/
│   ├── churn_analysis.ipynb     # notebook complet (code + résultats)
│   └── churn_analysis.html      # export HTML pour lecture sans Jupyter
├── outputs/
│   └── figures/                 # graphiques exportés en PNG
├── requirements.txt
└── README.md
```

## Démarche

<<<<<<< HEAD
1. **Compréhension du dataset** — dimensions, types, distribution de la cible.
=======
1. 
>>>>>>> 87d8b422d2877a3526f7c0609c3d6f4d55abce81
2. **Nettoyage** — conversion de `TotalCharges` en numérique, gestion des valeurs manquantes (clients à `tenure = 0`), suppression de `customerID` des features.
3. **EDA / visualisations** — distribution du churn, lien avec l'ancienneté, les charges mensuelles, le type de contrat et le service internet, matrice de corrélation.
4. **Prétraitement** — encodage one-hot des variables catégorielles, split train/test stratifié (80/20), standardisation pour la régression logistique.
5. **Modélisation** — deux modèles entraînés avec `class_weight='balanced'` (la cible est déséquilibrée : ~27% de churn) :
   - **Régression Logistique** (baseline interprétable)
   - **Random Forest** (300 arbres, profondeur max 8)
6. **Comparaison des modèles** — accuracy, précision, rappel, F1-score, ROC AUC, courbes ROC.
7. **Interprétation** — coefficients de la régression logistique et importance des variables du Random Forest, avec lecture métier.

## Résultats

| Modèle | Accuracy | Précision | Rappel | F1-score | ROC AUC |
|---|---|---|---|---|---|
| Régression Logistique | 0.74 | 0.51 | 0.79 | 0.62 | 0.841 |
| Random Forest | 0.76 | 0.53 | 0.78 | 0.63 | 0.844 |

Le **Random Forest** offre un léger avantage global (meilleure accuracy et AUC), mais la **régression logistique** reste précieuse pour la lecture directe de l'effet de chaque variable.

### Principaux facteurs de churn identifiés
- Contrat **mensuel** (`Month-to-month`) : facteur le plus déterminant.
- **Faible ancienneté** (`tenure`) : les nouveaux clients résilient davantage.
- **Absence de services de sécurité/support** (`OnlineSecurity`, `TechSupport`).
- **Charges mensuelles élevées** et service **Fibre optique**.

## Lancer le projet

```bash
python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/churn_analysis.ipynb
```



- Tester Gradient Boosting / XGBoost.
- Optimiser les hyperparamètres (GridSearchCV).
- Traiter le déséquilibre de classes avec SMOTE.
- Ajuster le seuil de décision selon le coût métier (faux négatif vs faux positif).
=======

>>>>>>> 87d8b422d2877a3526f7c0609c3d6f4d55abce81
