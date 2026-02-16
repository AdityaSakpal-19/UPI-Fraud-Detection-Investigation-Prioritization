# UPI Fraud Detection & Investigation Prioritization System

## Overview
This project simulates a fraud monitoring system for a digital payments (UPI) application.

Instead of only predicting fraud, the goal is operational:

> Fraud teams cannot review every alert — they must decide which transactions to investigate first.

The system combines rule-based detection and machine learning to improve investigation efficiency and generate explainable alerts.

---

## Business Objective
Build a workflow that:

- Identifies suspicious transactions
- Prioritizes investigator workload
- Improves review efficiency
- Produces clear investigation notes

---

## System Workflow

Transaction → Risk Signals → Rule Score → ML Ranking → Priority Queue → Investigator Notes

---

## Data Model
Relational tables simulate a production analytics environment:

| Table | Purpose |
|------|------|
| transactions | payment events |
| users | customer behavior profile |
| behavior_signals | risk indicators |

Data is extracted using SQL and analyzed using Python.

---

## Detection Logic

### Rule-Based Risk Signals
The system flags suspicious behavior using operational rules:

- unusually high transaction amount
- deviation from normal behavior
- late-night activity

```python
df['risk_score'] = (
    (df['amount_deviation'] > 1.8) * 50 +
    (df['high_amount'] == 1) * 30 +
    (df['late_night_txn'] == 1) * 20
)
