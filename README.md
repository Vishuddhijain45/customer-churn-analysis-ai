# Customer Churn Analysis and Prediction

**AICTE | IBM SkillsBuild – Data Analytics with AI Internship 2026**  
**Prepared by:** Vishuddhi Jain  
**Program:** B.Tech Information Technology, Jaypee Institute of Information Technology, Noida

## Project description

A telecom company loses revenue when customers stop using its services. This project explores customer data to identify patterns associated with churn and trains machine-learning classifiers to estimate which customers may be at risk. The intended use is to help a retention team prioritize customer-support and retention actions; model predictions should be reviewed rather than treated as certain outcomes.

The notebook covers data validation and cleaning, exploratory data analysis, feature preparation, comparison of three classification models, evaluation, feature importance, and risk-band summaries.

## Dataset

**IBM Telco Customer Churn** contains 7,043 customer records and 21 columns, including service subscriptions, contract type, payment method, tenure, monthly/total charges, and the churn label.

- Dataset repository: <https://github.com/IBM/telco-customer-churn-on-icp4d/blob/master/data/Telco-Customer-Churn.csv>
- Direct CSV download: <https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv>

The notebook downloads the dataset automatically when connected to the internet. For offline execution, download the CSV and put it in the same folder as the notebook with the exact name `Telco-Customer-Churn.csv`.

## Technologies used

- Python 3.10+
- pandas and NumPy for data handling
- Matplotlib and Seaborn for visualizations
- scikit-learn for preprocessing, Logistic Regression, Random Forest, Gradient Boosting, cross-validation, and evaluation metrics
- Jupyter Notebook / IPython kernel

## Setup and run

Open a terminal in the folder containing the four submission files.

```bash
# (Optional) create and activate a virtual environment
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# macOS/Linux:
source .venv/bin/activate

# Install the project dependencies
python -m pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

Open `VishuddhiJain_CustomerChurnAnalysis.ipynb`, then choose **Kernel → Restart Kernel and Run All Cells**. The notebook creates an `images/` folder for charts. Running all cells requires an internet connection unless the CSV has been downloaded locally as described above.

## Results from the notebook's saved run

The following metrics are included in the notebook/report's saved run. Re-run all cells to refresh outputs after any code or dependency changes.

| Model | Accuracy | Precision (churn) | Recall (churn) | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.738 | 0.504 | 0.783 | 0.614 | 0.842 |
| Random Forest | 0.774 | 0.556 | 0.749 | 0.638 | 0.844 |
| Gradient Boosting | 0.798 | 0.655 | 0.508 | 0.572 | 0.842 |

Random Forest had the strongest F1 score in the saved comparison and retained about 75% recall for churners, making it a reasonable demonstration model when balancing missed churners and false alarms. These are results for one stratified 80/20 split, not a guarantee of future performance.

### Main patterns in the data

- Overall churn rate: 26.5% (1,869 of 7,043 customers).
- Month-to-month contract churn: 42.7%; one-year: 11.3%; two-year: 2.8%.
- Fiber optic churn: 41.9%, compared with 19.0% for DSL.
- Electronic-check churn: 45.3%, compared with about 15–19% for other payment methods.
- Customers without tech support or online security churn at roughly 42%, compared with about 15% among customers with these services.
- Churn is highest in the first year (about 47.4% for the 0–12 month group) and lower among long-tenure customers.

Association does not establish causation. These findings should guide further investigation, not be treated as proof that a feature causes churn.

## Submission files

| File | Purpose |
|---|---|
| `VishuddhiJain_CustomerChurnAnalysis.ipynb` | Notebook with the project workflow and saved outputs |
| `requirements.txt` | Python libraries and dependencies |
| `VishuddhiJain_ProjectReport.docx` | Project report |
| `README.md` | Dataset, setup/run guide, results, and limitations |

## Limitations and responsible use

The dataset is a single historical snapshot. Predictions identify statistical associations; they do not prove why an individual customer might leave. The saved metrics reflect one split and may vary with library versions or a new run. For rigorous model selection, use cross-validation or a validation set to select the model, then evaluate it once on an untouched test set. Before real deployment, assess calibration, fairness, business costs, and performance on more recent data.
