# Privacy-Aware Data Pipeline

A Python-based data engineering project that validates, transforms, protects, and publishes customer transaction data into a privacy-aware analytical dataset.

## Project Overview

This project demonstrates an end-to-end data pipeline using synthetic customer and transaction data. It focuses on data quality, privacy protection, data minimization, reliable publishing, audit tracking, and scalability testing.

The pipeline prepares analytical data while avoiding the exposure of unnecessary personally identifiable information (PII).

## Architecture

```text
Synthetic Source Data
        |
        v
Data Profiling
        |
        v
Data Validation
        |
        +------ Invalid Records
        |              |
        |              v
        |          Quarantine
        |
        v
Valid Records
        |
        v
Privacy Transformation
(Masking & Tokenization)
        |
        v
Data Minimization
        |
        v
SQLite Analytical Warehouse
        |
        v
Audit & Data Quality Checks
```

## Key Features

- **Synthetic Data Generation:** Generates customer and transaction datasets for reproducible testing.
- **Data Profiling:** Analyzes data types, missing values, unique values, and data quality.
- **Data Validation:** Checks required fields, duplicate identifiers, invalid values, and customer references.
- **Quarantine Management:** Separates rejected records and records rejection details.
- **Privacy Protection:** Masks email addresses and phone numbers and applies SHA-256-based deterministic tokenization.
- **Data Minimization:** Removes unnecessary customer identifiers and sensitive fields before analytical publishing.
- **Database Publishing:** Publishes analytical records into SQLite.
- **Idempotent Publishing:** Uses database upserts and unique transaction identifiers to prevent duplicate records on reruns.
- **Audit Tracking:** Records pipeline execution details, record counts, rejected records, and execution status.
- **Testing:** Includes validation checks, negative test cases, database constraints, and data reconciliation.
- **Scalability Testing:** Tests the pipeline with 100,000 synthetic transactions.

## Technologies Used

- Python
- Pandas
- Faker
- SQLite
- Jupyter Notebook
- SQL
- hashlib
- Git and GitHub

## Project Structure

```text
privacy-aware-data-pipeline/
│
├── data/
│   └── .gitkeep
│
├── src/
│   └── .gitkeep
│
├── tests/
│   └── .gitkeep
│
├── notebooks/
│   └── .gitkeep
│
├── 01_understanding_the_data_public.ipynb
├── .gitignore
└── README.md
```

Generated datasets, local databases, and reports are excluded from GitHub through `.gitignore`.

The current implementation and execution workflow are documented in the Jupyter Notebook.

## Sample Results

### Data Validation

| Metric | Result |
|---|---:|
| Input customers | 100 |
| Valid customers | 98 |
| Rejected customers | 2 |
| Input transactions | 1,000 |
| Valid transactions | 984 |
| Rejected transactions | 16 |

### Privacy Transformation

- Email masking
- Phone number masking
- SHA-256-based customer tokenization
- Removal of unnecessary sensitive fields from the analytical dataset

### Analytical Dataset

| Metric | Result |
|---|---:|
| Published records | 984 |
| Analytical columns | 7 |
| Missing customer tokens | 0 |
| Duplicate transaction IDs | 0 |

### Scalability Results

| Metric | Result |
|---|---:|
| Customers generated | 10,000 |
| Transactions generated | 100,000 |
| Data generation time | 2.03 seconds |
| Database publishing time | 0.68 seconds |
| Publishing throughput | 146,817 records/second |
| Published records | 100,000 |

*Performance figures are from a local SQLite benchmark and depend on the hardware and execution environment.*

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/SV-181002/privacy-aware-data-pipeline.git
```

### 2. Navigate to the project directory

```bash
cd privacy-aware-data-pipeline
```

### 3. Install dependencies

```bash
pip install pandas faker jupyter
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

Open `01_understanding_the_data_public.ipynb` and execute the cells sequentially.

The notebook generates synthetic datasets and performs profiling, validation, privacy transformations, database publishing, testing, and scalability checks.

## Privacy and Security Notes

This project uses synthetic data and demonstrates privacy-aware data preparation.

SHA-256 tokenization provides deterministic pseudonymization, not encryption or guaranteed anonymization. Production systems should consider keyed HMAC or secure tokenization services, access controls, encryption, and appropriate privacy governance.

## Future Improvements

- Modularize notebook logic into reusable Python source modules.
- Add a formal automated test suite using pytest.
- Implement configurable privacy policies.
- Introduce workflow orchestration and retry handling.
- Add structured logging and monitoring.
- Integrate cloud-based storage and analytical warehouses.

## Author

**Durgampudi S V Krishna Reddy**

GitHub: https://github.com/SV-181002

LinkedIn: https://www.linkedin.com/in/durgampudisvkrishnareddy484362252/

---

*Built as a hands-on data engineering project focused on privacy-aware data processing, data quality, and scalable analytical publishing.*
