# Renewal Risk Intelligence Engine

An AI‑augmented prototype that helps BizOps teams identify at‑risk account renewals before they happen. It ingests multi‑modal data (structured CSVs, messy CSM notes, and product changelogs), computes a weighted risk score, and generates actionable, plain‑English explanations – all in a single Colab notebook.

---

## 🚀 Features

- **Unified Data Reconciliation** – Merges accounts, usage, support, NPS, and messy CSM notes using `pandas` and regex.
- **Hybrid Risk Scoring** – Combines usage trends, ticket load, and NPS into a 0–100 score, with CSM sentiment boosting or lowering the final tier.
- **Explainable Outputs** – Every at‑risk account receives a plain‑English summary of *why* it’s flagged and a specific action for the CSM.
- **Non‑Obvious Insight** – Automatically flags accounts that appear *low‑risk* numerically but are running on deprecated SDKs (v3.x) that will lose security patches on April 30, 2026.
- **Visual Dashboard** – Includes a risk distribution bar chart and an executive action playbook.

---

## 🧠 How It Works

| Step | Description |
|------|-------------|
| **1. Load & Filter** | Load all 6 data files and filter to accounts renewing within the next 90 days. |
| **2. Feature Engineering** | Compute usage trend (slope), total/open tickets, average NPS, and parse SDK versions. |
| **3. Risk Scoring** | Normalize features and apply a weighted composite score: `40% Usage + 35% Support + 25% NPS`. |
| **4. CSM Signal Extraction** | Parse unstructured call notes with a smart heuristic (keyword matching) to extract sentiment, risk signals, and recommended actions. *(The architecture also supports LLM integration – see below.)* |
| **5. Insight & Export** | Surface hidden risks (e.g., SDK deprecation) and generate a prioritized action playbook. |

---

## 📂 Project Structure

renewal-risk-intelligence-engine/
├── renewal_risk_engine.ipynb # Main Colab notebook (run this)
├── README.md # This file
└── requirements.txt # Python dependencie

---

## ⚙️ Setup & Running (For Evaluators)

### Option A: Google Colab (Recommended – Zero Setup)
1. Open the notebook in Google Colab.
2. Upload the 6 data files (`accounts.csv`, `usage_metrics.csv`, `support_tickets.csv`, `csm_notes.txt`, `nps_responses.csv`, `changelog.md`) to the Colab runtime.
3. Run all cells sequentially (`Runtime → Run all`).
4. Scroll to the bottom to see:
   - Risk distribution chart
   - Top 5 at‑risk accounts with explanations
   - CSM Action Playbook
   - Executive Alert for non‑obvious SDK risks

### Option B: Local Environment

# Clone and install
git clone https://github.com/yourusername/renewal-risk-intelligence-engine.git
cd renewal-risk-intelligence-engine
pip install -r requirements.txt

# Run the notebook (requires Jupyter or VS Code)
jupyter notebook renewal_risk_engine.ipynb
