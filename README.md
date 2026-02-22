# Financial Fraud Detection System

A simple Python tool that detects financial fraud using Benford's Law and financial ratio analysis.

## What It Does
- Analyzes company financial data
- Checks if numbers follow Benford's Law (natural pattern)
- Detects suspicious financial ratios
- Scores fraud probability (0-100%)

## Quick Start

### Install Requirements
```bash
pip install pandas numpy scipy
```

### Run Analysis
```bash
python fraud_detector.py
```

### Output
```
Normal Corp
Fraud Score: 15.3%
Risk Level: LOW
✓ No red flags detected

Suspicious Inc
Fraud Score: 78.2%
Risk Level: HIGH
Red Flags (3):
  ⚠ Suspiciously high margin (60%)
  ⚠ High AR/Revenue (60%)
  ⚠ Assets growing much faster than revenue
```

## How It Works

### 1. Benford's Law Check
Real financial data follows predictable first-digit patterns. Fraudulent data doesn't.

### 2. Red Flag Detection
Checks for:
- Revenue growing >50% per year
- Accounts Receivable > 40% of revenue
- Profit margins > 40%
- Assets growing faster than revenue

### 3. Fraud Scoring
Combines signals:
- Benford's Law violation: 0-40 points
- Red flags: 10 points each
- Total: 0-100%

## Risk Levels
- **LOW** (0-30%): Normal company
- **MEDIUM** (30-60%): Monitor closely
- **HIGH** (60-100%): Likely fraud

## Example Usage
```python
from fraud_detector import analyze_company

# Analyze a company
fraud_score, risk_level, red_flags = analyze_company(
    company_name="My Company",
    revenue=1000000,
    net_income=250000,
    assets=2000000,
    accounts_receivable=250000,
    prev_revenue=900000,
    prev_assets=1800000
)

print(f"Fraud Score: {fraud_score}%")
print(f"Risk Level: {risk_level}")
```

## Database
Results are automatically saved to `fraud_detector.db` (SQLite)

## Skills Demonstrated
- ✓ Statistical analysis (Benford's Law, chi-square test)
- ✓ Financial analysis (ratio calculation, red flag detection)
- ✓ Database design (SQLite)
- ✓ Python (pandas, numpy, scipy)
- ✓ Object-oriented programming

## Real-World Applications
This technique is used by:
- Auditors (Big 4: Deloitte, EY, KPMG, PWC)
- Forensic accountants
- Compliance teams
- SEC investigators

## Future Enhancements
- Web interface (Flask/Streamlit)
- Real SEC data integration
- Machine learning models
- Visualization dashboards
```

**3. `requirements.txt`** (dependencies)
```
pandas>=1.3.0
numpy>=1.21.0
scipy>=1.7.0
```

**4. `.gitignore`** (don't upload these)
```
__pycache__/
*.pyc
*.db
.DS_Store
.venv/
