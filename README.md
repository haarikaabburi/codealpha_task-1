💳 Credit Scoring Model
CodeAlpha Machine Learning Internship — Task 1
📌 Objective
Predict an individual's creditworthiness (likelihood of loan default) using historical financial data.
The model helps financial institutions make informed lending decisions by classifying applicants as creditworthy or likely to default.

🗂️ Project Structure
CodeAlpha_CreditScoringModel/
│
├── credit_scoring_model.py          # Main pipeline script
│
├── outputs/
│   ├── 01_class_distribution.png    # EDA: class balance
│   ├── 02_correlation_heatmap.png   # EDA: feature correlations
│   ├── 03_roc_curves.png            # ROC-AUC for all models
│   ├── 04_confusion_matrix_*.png    # Confusion matrix (best model)
│   ├── 05_feature_importance.png    # Random Forest feature importances
│   └── 06_model_comparison.png      # All models side-by-side
│
└── README.md

📊 Dataset
The project uses a synthetic dataset that mirrors real-world credit scoring features.
To use a real dataset, replace the data generation block with:
pythondf = pd.read_csv("cs-training.csv")   # Kaggle: Give Me Some Credit
Features used:
FeatureDescriptionageApplicant's ageincomeAnnual incomeemployment_yearsYears in current employmentnum_credit_linesNumber of open credit linesoutstanding_debtTotal outstanding debtdebt_to_income_ratioDebt as a fraction of incomenum_late_paymentsCount of late paymentsnum_defaultsNumber of prior defaultscredit_utilizationRatio of used credit to limitnum_inquiriesCredit inquiries in last 12 monthsmonths_since_last_delinquencyRecency of last missed paymenthome_ownershipRENT / OWN / MORTGAGEloan_purposeReason for the loan
Engineered Features:
FeatureFormulaincome_to_debt_ratioincome / (outstanding_debt + 1)payment_history_score1 / (late_payments + defaults + 1)credit_risk_indexdebt_to_income_ratio × credit_utilizationfinancial_stability_scoreemployment_years × income / 1e6

🤖 Models Trained
ModelLibraryLogistic Regressionsklearn.linear_modelDecision Treesklearn.treeRandom Forestsklearn.ensembleGradient Boostingsklearn.ensemble
All models are wrapped in Scikit-learn Pipelines with imputation and scaling built in.

📈 Evaluation Metrics

Accuracy — Overall correct predictions
Precision — Of predicted defaults, how many were real
Recall — Of actual defaults, how many were caught
F1-Score — Harmonic mean of Precision & Recall
ROC-AUC — Ability to distinguish creditworthy vs default
5-Fold Stratified Cross-Validation — Stability check

Results
ModelAccuracyPrecisionRecallF1-ScoreROC-AUCLogistic Regression~0.98~0.97~0.96~0.97~0.99Decision Tree~0.95~0.93~0.92~0.93~0.96Random Forest~0.97~0.96~0.95~0.96~0.98Gradient Boosting~0.97~0.96~0.94~0.95~0.98

🏆 Best Model: Logistic Regression (ROC-AUC ≈ 0.987, 5-Fold CV AUC ≈ 0.984 ± 0.003)


📉 Visualizations
PlotDescriptionClass DistributionBalance between default vs creditworthyCorrelation HeatmapFeature relationshipsROC CurvesAll 4 models comparedConfusion MatrixBest model prediction breakdownFeature ImportanceTop 15 features by Random ForestModel ComparisonBar chart of all metrics across models

🚀 How to Run
1. Clone the Repository
bashgit clone https://github.com/<your-username>/CodeAlpha_CreditScoringModel.git
cd CodeAlpha_CreditScoringModel
2. Install Dependencies
bashpip install scikit-learn pandas numpy matplotlib seaborn
3. Run the Script
bashpython credit_scoring_model.py
All output plots are saved in the current directory.

🔁 Using a Real Dataset (Optional)

Download Give Me Some Credit from Kaggle
Place cs-training.csv in the project folder
Replace the generate_credit_dataset() call in main() with:

pythondf = pd.read_csv("cs-training.csv")
df.rename(columns={"SeriousDlqin2yrs": "default"}, inplace=True)
df.dropna(inplace=True)

🛠️ Tech Stack
LibraryPurposePython 3.8+Core languageScikit-learnML models, metrics, pipelinesPandasData manipulationNumPyNumerical operationsMatplotlibPlottingSeabornStatistical visualizations

👨‍💻 Author
Abburi Harika
Machine Learning Intern — CodeAlpha
🔗 LinkedIn | 🐙 GitHub

🏢 Internship
This project was completed as part of the CodeAlpha Machine Learning Internship.
