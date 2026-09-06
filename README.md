# 🏥 Papollo Hospitals — Patient & Billing Dashboard (Power BI)

An interactive **Power BI dashboard** built for Papollo Hospitals to track patient admissions, bed occupancy, billing, insurance claims, and doctor performance — all from a single, filterable view.

---

## 📌 Business Problem

A multi-department hospital like Papollo generates patient-level data across admission, diagnosis, treatment, billing, and follow-up — but that data is only useful if hospital administrators can actually **see it, filter it, and act on it quickly**.

Without a consolidated view, hospital staff struggle to answer basic operational questions in real time:

> **"For any given patient (or time period), what's their admission/discharge/follow-up timeline, what did they get billed, how full are our beds, which doctors are getting the most patient feedback, and which diagnoses are most common?"**

This project solves that by turning a raw patient records spreadsheet into a **live, filterable dashboard** that lets staff:
- Look up any patient by ID and instantly see their admit date, discharge date, follow-up date, and total bill
- Monitor **bed occupancy** across General, ICU, and Private wards
- Track **billing vs. insurance coverage** trends alongside tests performed
- See **diagnosis-wise patient volume** to spot which conditions are most common
- Review **feedback volume per doctor**, as a proxy for doctor workload/patient satisfaction
- Filter everything by **date range** and **patient**, so any of the above can be sliced on demand

---

## 🧰 Tools Used

| Tool | Purpose |
|---|---|
| **Microsoft Excel** | Source data (`Papollo-Healtcare-Dataset.xlsx`) |
| **Power BI Desktop** | Data modeling, DAX aggregations, and dashboard/report design |
| **Power Query** | Loading and shaping the raw patient data inside Power BI |

---

## 🗂️ Project Structure

```
papollo_powerbi_project/
├── Papollo.pbix                        # Power BI report file
├── Papollo-Healtcare-Dataset.xlsx      # Source patient records dataset
└── README.md
```

---

## 📊 Dataset

The source file `Papollo-Healtcare-Dataset.xlsx` contains **7,157 patient records** with the following fields:

| Column | Description |
|---|---|
| `Patient_ID` | Unique identifier per patient |
| `Admit_Date` | Date the patient was admitted |
| `Discharge_Date` | Date the patient was discharged |
| `Diagnosis` | Condition diagnosed (e.g. Viral Infection, Typhoid, Malaria, Flu, Pneumonia, Fracture) |
| `Bed_Occupancy` | Ward type occupied — General, ICU, or Private |
| `Test` | Test performed — MRI, CT Scan, X-Ray, Blood Test, Ultrasound |
| `Doctor` | Attending doctor |
| `Followup Date` | Scheduled follow-up date (a small number of records have no follow-up scheduled) |
| `Feedback` | Patient feedback/satisfaction score (ranges 3.5–5.0) |
| `Billing Amount` | Total amount billed (ranges roughly ₹1,200 to ₹95,900) |
| `Health Insurance Amount` | Portion of the bill covered by insurance |

Records span admissions from **December 2022 through March 2024**.

---

## 🛠️ How This Project Was Built

### 1. Data Preparation
- Patient records were sourced as an Excel workbook (`Papollo-Healtcare-Dataset.xlsx`, sheet `Sheet1`).
- The data was imported into **Power BI Desktop** and loaded into the data model as a single table (`Sheet1`) covering all 11 fields listed above.

### 2. Report Design
The report (`Papollo.pbix`) is built as a single dashboard page, **"Papollo Hospitals: Leads Flow Dashboard,"** combining KPI cards, charts, images, and interactive filters:

**Header & Branding**
- Title textbox and hospital logo/images placed at the top of the report

**KPI Cards** (dynamically update based on filters/slicers)
- **Admit Date** — earliest admit date in the current selection
- **Discharge Date** — earliest discharge date in the current selection
- **Follow Up Date** — earliest follow-up date in the current selection
- **Bill Amount** — sum of billing amount in the current selection

**Charts**
- **Bed Occupancy** — column chart showing patient counts by ward type (General/ICU/Private)
- **Bed Occupancy trend** — line chart relating Health Insurance Amount, Test, and Billing Amount
- **Feedback Volume per Doctor** — donut chart showing how patient feedback is distributed across doctors
- **Diagnosis-wise Patient Count** — funnel chart ranking diagnoses by patient volume

**Interactivity (Slicers)**
- Filter by **Patient_ID** — drill into a single patient's record
- Filter by **Admit Date / Date Range** — analyze a specific time window

### 3. Interaction Flow
Selecting a patient (or date range) in the slicers instantly updates every card and chart on the page — so a staff member can either explore hospital-wide trends or drill into one patient's full record, using the same dashboard.

---

## 🔎 Key Insights

- Billing amounts vary widely (₹1,200–₹95,900 per patient), with a median around ₹12,300 — driven largely by diagnosis severity and tests performed
- A small number of patients (~122 out of 7,157) have no follow-up date scheduled, which is worth flagging operationally
- Bed occupancy is split across General, ICU, and Private wards, giving a quick read on capacity pressure by ward type
- Doctor-level feedback volume highlights which doctors are seeing (and being rated by) the most patients
- Diagnosis distribution (Viral Infection, Typhoid, Malaria, Flu, Pneumonia, Fracture) shows which conditions drive the most hospital visits, useful for resourcing and inventory planning

---

## ✅ Recommendations

**For Hospital Administration**
- Use the diagnosis funnel to plan staffing/inventory around the most common conditions
- Monitor the ICU vs. General vs. Private occupancy split to anticipate capacity bottlenecks
- Flag and follow up on the patients missing a scheduled follow-up date

**For Billing/Insurance Teams**
- Use the Billing Amount vs. Health Insurance Amount relationship to spot cases with unusually low insurance coverage
- Segment high-billing patients by diagnosis/test to understand cost drivers

---

## 📝 Conclusion

This project turns a raw hospital patient-records spreadsheet into a single, interactive Power BI dashboard that hospital staff can use to monitor admissions, billing, bed occupancy, and doctor feedback — answering real operational questions (capacity, cost, follow-up compliance, doctor load) without needing to dig through spreadsheets manually.
