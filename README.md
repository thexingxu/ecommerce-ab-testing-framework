# E-Commerce Conversion Rate Optimization: End-to-End A/B Testing Framework

An enterprise-grade statistical experimentation framework and decision-gate pipeline analyzing 290,000+ unique user sessions to evaluate a landing page redesign.

---

## 🎯 Executive Summary

* **Business Objective:** Determine whether a redesigned landing page produces a statistically significant lift in conversion rates across 290,000+ users without introducing sample bias or regional cannibalization.
* **Core Conclusion:** **Do Not Roll Out (Full Rollback Recommended)**.
* **Key Finding:** The treatment variant failed to demonstrate positive lift ($\Delta = -0.158\%$ points; two-sided pooled $Z$-test $p = 0.1899$). Logistic regression interaction models confirmed the absence of heterogeneous treatment effects across geographic markets ($p > 0.40$). Deploying the new design introduces technical debt with zero measurable conversion upside.

---

## 🏗️ Experiment Architecture

```text
ecommerce-ab-testing-framework/
├── data/
│   ├── ab_data.csv                    <- Raw session and conversion event logs
│   ├── countries.csv                  <- Regional metadata mapping
│   └── clean_ab_data.parquet          <- Sanitized, audit-verified experimental cohort
├── notebooks/
│   ├── 01_power_analysis_and_srm.ipynb <- Pre-test sizing, MDE curves & SRM diagnostics
│   ├── 02_hypothesis_testing_and_lift.ipynb <- Z-tests, 95% CIs & 10,000-sample bootstrap
│   └── 03_segmentation_and_rollout.ipynb <- Regional segmentation & logistic interaction models
├── requirements.txt
└── README.md