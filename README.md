# AI-Powered Insider Threat Detection System

A behavioural anomaly detection tool that analyses enterprise user activity logs 
to identify potential insider threats, powered by AI-generated threat assessments.

## What It Does
- Profiles 1000+ users across 4 million+ log events
- Scores each user 0-100 based on behavioural deviation from their personal baseline
- Automatically generates SOC-ready threat reports using the Claude API
- Visualises results in an interactive dashboard

## Detection Approach

Built a three-model ensemble where each model targets a different insider threat archetype:

| Model | Targets | Signal Used |
|-------|---------|-------------|
| Model 1 | Extreme after-hours access | After-hours ratio + volatility |
| Model 2 | Multi-signal anomalies | Percentile rank across all signals |
| Model 3 | USB/file exfiltration | Signal count thresholds |

### Results Against Ground Truth (CERT r4.2 Answer Key)

| Version | Approach | Detected | Flagged |
|---------|----------|----------|---------|
| v1 | Volume-based | 0/70 (0%) | 10 |
| v2 | Baseline deviation | 12/70 (17%) | 70 |
| v3 | Multi-model ensemble | 42/70 (60%) | 133 |

**Key finding:** Real insider threats deliberately stay within normal usage ranges. 
A single model cannot catch all threat archetypes — different attack patterns 
require different detection strategies.

## Tech Stack
- Python, Pandas
- Anthropic Claude API
- HTML/CSS Dashboard
- Dataset: CERT Insider Threat Dataset r4.2 — Carnegie Mellon University

## Key Files
- `Insider Threat Detection.ipynb` — Full analysis and detection pipeline
- `dashboard.html` — Interactive threat dashboard
- `threat_reports.json` — AI-generated threat assessments

---

## Future Plans

- [ ] Run formal sklearn evaluation metrics (precision_score, recall_score, confusion_matrix) and publish results
- [ ] Tune ensemble thresholds to improve precision beyond current 31.6%
- [ ] Add time-series analysis to detect gradual behavioural escalation over weeks
- [ ] Test against real enterprise log data rather than simulated dataset
- [ ] Integrate with a SIEM (Splunk/Microsoft Sentinel) for live alert ingestion

## Setup
1. Clone the repo
2. Create a `.env` file with your `ANTHROPIC_API_KEY`
3. Download CERT r4.2 dataset from https://kilthub.cmu.edu/articles/dataset/Insider_Threat_Test_Dataset/12841247
4. Run the notebook
