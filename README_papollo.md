# Papollo Power BI Project

A Power BI dashboard analyzing patient admissions, treatments, billing, and insurance data for Papollo Healthcare.

## Overview

This project turns a raw hospital dataset into an interactive Power BI report, giving visibility into patient stays, diagnoses, doctor workload, test volumes, billing amounts, and insurance coverage. It's aimed at helping hospital administrators track operational and financial performance at a glance.

## Dataset

**File:** `Papollo-Healtcare-Dataset.xlsx` (~7,150 patient records)

| Column | Description |
|---|---|
| `Patient_ID` | Unique identifier for the patient |
| `Admit_Date` | Date the patient was admitted |
| `Discharge_Date` | Date the patient was discharged |
| `Diagnosis` | Recorded diagnosis (e.g. Viral Infection, Typhoid, Malaria) |
| `Bed_Occupancy` | Ward type (e.g. General, ICU) |
| `Test` | Test administered (e.g. MRI, CT Scan) |
| `Doctor` | Attending doctor |
| `Followup Date` | Scheduled follow-up date |
| `Feedback` | Patient feedback score |
| `Billing Amount` | Total amount billed |
| `Health Insurance Amount` | Amount covered by insurance |

## Dashboard

**File:** `Papollo.pbix`

Built in Power BI Desktop, the report connects to the dataset above and is designed to surface:
- Patient admission and discharge trends over time
- Length of stay by diagnosis and ward type (General vs. ICU)
- Test volumes and doctor caseloads
- Billing amount vs. insurance-covered amount
- Patient feedback scores

