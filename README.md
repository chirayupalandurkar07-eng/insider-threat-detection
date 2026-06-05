# AI-Powered Insider Threat Detection System

A behavioural anomaly detection tool that analyses enterprise user activity logs 
to identify potential insider threats, powered by AI-generated threat assessments.

## What It Does
- Profiles 1000+ users across 4 million+ log events
- Scores each user 0-100 based on behavioural deviation from their personal baseline
- Automatically generates SOC-ready threat reports using the Claude API
- Visualises results in an interactive dashboard

## Detection Approach
Initial volume-based scoring flagged 0 of 70 known malicious users, revealing 
that real insider threats deliberately stay within normal usage ranges. 
The model was rebuilt using deviation-from-personal-baseline scoring, 
improving detection to 12 of 70 known malicious users using logon behaviour alone.

## Tech Stack
- Python, Pandas
- Anthropic Claude API
- HTML/CSS Dashboard
- Dataset: CERT Insider Threat Dataset r4.2 — Carnegie Mellon University

## Key Files
- `Insider Threat Detection.ipynb` — Full analysis and detection pipeline
- `dashboard.html` — Interactive threat dashboard
- `threat_reports.json` — AI-generated threat assessments

## Setup
1. Clone the repo
2. Create a `.env` file with your `ANTHROPIC_API_KEY`
3. Download CERT r4.2 dataset from https://kilthub.cmu.edu/articles/dataset/Insider_Threat_Test_Dataset/12841247
4. Run the notebook
