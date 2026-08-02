# 🔍 Renewal Risk Intelligence Engine

An AI-powered prototype that helps Business Operations (BizOps) and Customer Success teams proactively identify customer accounts at risk of not renewing. The system combines structured business metrics with unstructured customer notes to generate explainable renewal risk scores and actionable recommendations.

Built as a single Google Colab notebook, the project demonstrates data engineering, feature engineering, risk modeling, NLP, and business intelligence in one workflow.

---

# ✨ Features

### 📊 Unified Data Processing

* Merges structured datasets including:

  * Customer accounts
  * Product usage metrics
  * Support tickets
  * NPS responses
* Cleans and processes messy CSM notes using regular expressions and text preprocessing.

### 📈 Hybrid Risk Scoring

Computes a weighted renewal risk score (0–100) using:

* **40%** Product Usage Trend
* **35%** Support Ticket Load
* **25%** Customer Satisfaction (NPS)

The final score is adjusted using insights extracted from Customer Success Manager (CSM) notes.

### 🧠 Explainable AI

Instead of only producing a score, the system explains:

* Why an account is considered at risk
* Which signals contributed most
* What action the Customer Success team should take

### 🚨 Hidden Risk Detection

Identifies accounts that appear healthy numerically but are running deprecated **SDK v3.x**, which will lose security support after **April 30, 2026**.

This helps surface risks traditional dashboards may miss.

### 📊 Executive Dashboard

The notebook generates:

* Risk distribution chart
* Top high-risk renewal accounts
* Executive action playbook
* Hidden SDK migration alerts

---

# ⚙️ Workflow

| Step                       | Description                                                                               |
| -------------------------- | ----------------------------------------------------------------------------------------- |
| **1. Data Loading**        | Load all input files and filter customers renewing within the next 90 days.               |
| **2. Feature Engineering** | Calculate usage trends, support metrics, average NPS, and extract SDK versions.           |
| **3. Risk Scoring**        | Generate a weighted composite risk score using normalized business metrics.               |
| **4. NLP Analysis**        | Analyze unstructured CSM notes using keyword-based sentiment and risk extraction.         |
| **5. Business Insights**   | Generate explainable summaries, recommended actions, and detect hidden SDK-related risks. |

---

# 🛠 Tech Stack

* Python
* Pandas
* NumPy
* Matplotlib
* Regular Expressions (Regex)
* Google Colab
* Natural Language Processing (Rule-based)

---

# 📁 Project Structure

```text
renewal-risk-intelligence-engine/
│
├── renewal_risk_engine.ipynb      # Main Google Colab notebook
├── README.md
├── requirements.txt
│
├── accounts.csv
├── usage_metrics.csv
├── support_tickets.csv
├── nps_responses.csv
├── csm_notes.txt
└── changelog.md
```

---

# 🚀 Getting Started

## Option 1: Google Colab (Recommended)

1. Open **renewal_risk_engine.ipynb** in Google Colab.
2. Upload the following files:

   * accounts.csv
   * usage_metrics.csv
   * support_tickets.csv
   * nps_responses.csv
   * csm_notes.txt
   * changelog.md
3. Select **Runtime → Run all**.
4. View the generated:

   * Risk distribution chart
   * Top at-risk accounts
   * Executive action playbook
   * SDK migration alerts

---

## Option 2: Run Locally

Clone the repository:

```bash
git clone https://github.com/<your-username>/renewal-risk-intelligence-engine.git
cd renewal-risk-intelligence-engine
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook renewal_risk_engine.ipynb
```

---

# 📤 Sample Outputs

The notebook produces:

* 📊 Renewal Risk Distribution
* 🚩 Top At-Risk Accounts
* 💡 Plain-English Risk Explanations
* ✅ Customer Success Action Recommendations
* ⚠️ Hidden SDK Deprecation Alerts

---

# 💡 Future Improvements

* Integrate an LLM (OpenAI, Ollama, or Gemini) for richer CSM note analysis.
* Replace rule-based sentiment with transformer-based models.
* Build an interactive Streamlit dashboard.
* Schedule automated risk monitoring with daily data refreshes.
* Export reports directly to Slack or email.


