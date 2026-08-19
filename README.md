# Hi, I’m Fadi Saif

### Analytics Professional | Data Analyst | BI & Decision Support

I am an analytics-focused professional with **10+ years of experience across humanitarian programmes, MEAL/MEL, operations, reporting, and data-informed decision support**. My primary interest is analytics: understanding operational questions, defining useful measures, interpreting evidence, and communicating insights clearly.

I use **engineering as a means to an end**. SQL, Python, data modeling, workflow automation, and modern data-stack practices help me make analytical work more reliable, repeatable, and easier to use—not replace the analytical purpose.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Fadi%20Saif-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/fadisaif) [![Email](https://img.shields.io/badge/Email-fadi.saif%40outlook.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:fadi.saif@outlook.com) [![GitHub](https://img.shields.io/badge/GitHub-FadiSaif--BA-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/FadiSaif-BA)

---

## What I work on

I work on analytical problems where data is fragmented, inconsistent, difficult to reproduce, or not yet structured for decision-making. My projects span humanitarian monitoring, operational reporting, business intelligence, sales analysis, data quality, geospatial analysis, and applied NLP.

| Area | Practical focus |
|---|---|
| **Analytics and decision support** | Translating operational questions into measures, analysis, reporting structures, and clear recommendations. |
| **SQL and data analysis** | More than 5 years of SQL experience across reporting, extraction, transformation, relational data work, and analytical modeling. |
| **Python for analytics** | 2–3 years of Python experience for data preparation, workflow automation, applied machine learning, and analytical experimentation. |
| **Modern data practices** | 2–3 years of focused experience with dimensional modeling, Medallion Architecture, Delta Lake, DuckDB, and workflow orchestration. |
| **Data quality and governance** | Standardizing identifiers, resolving duplicates, validating relationships, preserving audit trails, and separating source observations from derived values. |
| **BI and visualization** | Preparing structured datasets and analytical models for Power BI and operational decision support. |

> **My focus is the insight and decision. Engineering is the means that makes the analysis more reliable and repeatable.**

---

## Selected projects

The table below gives a quick overview of the portfolio. The detailed case studies that follow explain the problem, approach, business value, and evidence for each project.

| Project | Problem addressed | Analytical or business value |
|---|---|---|
| [SEAL Data Lakehouse](https://github.com/FadiSaif-BA/SEAL-DataLakehouse) | Assessment and reference data came from different systems and spreadsheet-based workflows, creating repeated cleaning and reproducibility challenges. | Provides a structured analytical foundation with clearer data lineage, quality controls, and reporting-ready models. |
| [ERP Sales Data Warehouse](https://github.com/FadiSaif-BA/DataPipeline_DataWarehouse) | Multi-year sales data was distributed across SQL Server ERP system databases and archives, making historical analysis more difficult. | Supports revenue, profitability, product, Pareto, customer, and market-basket analysis in an isolated analytical environment. |
| [Geospatial GPS Imputation](https://github.com/FadiSaif-BA/Geospatial-GPS-Imputation) | Missing, imprecise, or invalid coordinates reduced the reliability of mapping and spatial monitoring. | Corrected or imputed approximately 1,600 documented records and provides a design that can be extended toward larger datasets. Reducing manual workload by over 70%, while seamlessly scaling to hundreds of thousands of records. |
| [Arabic-to-English Transliteration](https://github.com/FadiSaif-BA/Transliteration-Model) | Inconsistent Arabic-to-English place-name conversion affected GIS matching, reporting, and downstream joins. | Supports more consistent multilingual data preparation through rules, applied NLP, and human review. |

### 1. [SEAL Data Lakehouse](https://github.com/FadiSaif-BA/SEAL-DataLakehouse)

**Problem.** Assessment submissions and institutional reference data came from different systems and spreadsheet-based workflows. Repeated cleaning, inconsistent identifiers, duplicate records, unreliable GPS observations, and limited traceability made it difficult to reproduce analytical outputs consistently.

**Approach.** I designed and documented a lightweight Medallion Architecture using Delta Lake, DuckDB, Python, and Prefect. The workflow separates raw ingestion, cleaning and standardization, analytical modeling, warehouse serving, and operational extraction. It includes persisted layer boundaries, schema controls, incremental API ingestion, surrogate identifiers, and referential-integrity quarantine.

**Business value.** The project provides a structured and auditable analytical foundation for monitoring and reporting. It supports more consistent school, district, supervisor, and assessment analysis while avoiding the need to introduce a heavyweight database-server environment for the documented operating context.

**Evidence.** The public repository documents an operating context involving 981 schools, 27 districts, 193 district supervisors, and more than 200,000 students. It also documents a Star Schema, DuckDB analytical serving, data-quality controls, and the exclusion of sensitive operational datasets from version control.

**Stack.** `Python` · `Delta Lake` · `DuckDB` · `Prefect` · `pandas` · `PyArrow` · `KoboToolbox API` · `Power BI` · `Star Schema`

[View repository →](https://github.com/FadiSaif-BA/SEAL-DataLakehouse)

### 2. [ERP Sales Data Warehouse](https://github.com/FadiSaif-BA/DataPipeline_DataWarehouse)

**Problem.** Multi-year sales data was distributed across legacy SQL Server ERP systems. This made historical analysis more difficult and created a risk that analytical queries would compete with transactional workloads.

**Approach.** I built a PostgreSQL ELT warehouse with Bronze, Silver, and Gold schemas. The workflow streams source data in batches, applies semantic naming and deduplication, enriches the product catalogue, normalizes financial metrics to SAR, and creates a Kimball-style Star Schema with verification checks.

**Business value.** The warehouse creates a reusable analytical foundation for revenue, profitability, product performance, Pareto, customer, and market-basket analysis. It also separates analytical workloads from the operational ERP environment and provides more consistent definitions for business reporting.

**Evidence.** The public repository documents enrichment of more than 22,000 spare parts, 18,028 sales line-item facts, 54-plus mapped entities, and 14 automated verification checks covering data-integrity conditions.

**Stack.** `PostgreSQL` · `Microsoft SQL Server` · `Python` · `SQL` · `pgloader` · `pyodbc` · `psycopg2` · `Dimensional Modeling` · `ELT`

[View repository →](https://github.com/FadiSaif-BA/DataPipeline_DataWarehouse)

### 3. [Geospatial GPS Imputation](https://github.com/FadiSaif-BA/Geospatial-GPS-Imputation)

**Problem.** Field survey systems can produce missing, imprecise, default, or out-of-bounds coordinates. These issues reduce the reliability of school-level mapping, GIS analysis, distance calculations, and spatial dashboards.

**Approach.** I implemented a three-tier cascade that uses trusted same-school observations first and distance-weighted KNN as a fallback for schools without usable historical coordinates. The process preserves original observations, records the source and quality of each coordinate, and is designed to integrate with the Silver layer of the Medallion Data Lakehouse.

**Business value.** The approach supports more usable spatial reporting and can reduce repetitive manual coordinate review. It also keeps estimated coordinates distinguishable from original field observations, which is important when spatial outputs inform monitoring or operational decisions.

**Evidence.** The documented evaluation corrected or imputed approximately **1,600 of 5,210 records**. The evaluated KNN configuration (`k=5`, distance-weighted) achieved a mean error of 1.0552 km, representing a 20.6% reduction relative to the evaluated `k=1` baseline. The processing design is structured for extension toward datasets of approximately **100,000 records**; the public evaluation itself covers the 5,210-record dataset.

**Stack.** `Python` · `scikit-learn` · `KNN` · `Random Forest` · `Inverse Distance Weighting` · `Haversine Distance` · `GIS` · `KoboToolbox API`

[View repository →](https://github.com/FadiSaif-BA/Geospatial-GPS-Imputation)

### 4. [Arabic-to-English Transliteration](https://github.com/FadiSaif-BA/Transliteration-Model)

**Problem.** Arabic administrative names can vary because of spelling, orthography, transliteration conventions, and inconsistent data entry. Manual conversion creates delays and makes GIS matching, reporting, searching, and downstream joins less consistent.

**Approach.** I developed a hybrid transliteration system in which deterministic rules handle predictable patterns and a Seq2Seq LSTM with attention handles more ambiguous phonetic mappings. The workflow includes Arabic normalization, model evaluation, beam-search decoding, and human review for uncertain outputs.

**Business value.** The project supports more consistent naming across multilingual operational datasets and can reduce repetitive preparation work before data is used in maps, reports, searches, and analytical models. Human validation remains part of the design where model certainty is insufficient.

**Evidence.** The public repository describes training data of approximately 81,000 name pairs and reports exact-match, functional, character, and contextual evaluation metrics on a test set of approximately 12,000 Yemeni place names. These figures should be interpreted together with their metric definitions and test-set context.

**Stack.** `Python` · `TensorFlow` · `Keras` · `Seq2Seq` · `LSTM` · `Bahdanau Attention` · `Arabic NLP` · `Text Normalization`

[View repository →](https://github.com/FadiSaif-BA/Transliteration-Model)

---

## Impact and working style

- I connect analytical work to programme, operational, financial, and reporting questions rather than treating technology as the objective.
- I use SQL as my strongest technical foundation and Python as a growing tool for automation, data preparation, and applied machine learning.
- I prefer transparent workflows that preserve source observations, document assumptions, and make unresolved records visible for review.
- I aim to produce analysis that is understandable to decision-makers and maintainable by the people who will use it after delivery.

---

## Technical toolkit

**Analytics and querying:**  
![SQL](https://img.shields.io/badge/SQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

**Data modeling and storage:**  
![Delta Lake](https://img.shields.io/badge/Delta_Lake-003366?style=flat-square)
![Star Schema](https://img.shields.io/badge/Star_Schema-4A5568?style=flat-square)
![Dimensional Modeling](https://img.shields.io/badge/Dimensional_Modeling-4A5568?style=flat-square)
![Medallion Architecture](https://img.shields.io/badge/Medallion_Architecture-0F766E?style=flat-square)

**Workflow and data preparation:**  
![Prefect](https://img.shields.io/badge/Prefect-024DFD?style=flat-square&logo=prefect&logoColor=white)
![REST APIs](https://img.shields.io/badge/REST_APIs-009688?style=flat-square)
![Data validation](https://img.shields.io/badge/Data_validation-475569?style=flat-square)
![Deduplication](https://img.shields.io/badge/Deduplication-475569?style=flat-square)
![Referential-integrity checks](https://img.shields.io/badge/Referential--integrity_checks-475569?style=flat-square)

**BI and reporting:**  
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![KPI design](https://img.shields.io/badge/KPI_design-0284C7?style=flat-square)
![Monitoring and evaluation analytics](https://img.shields.io/badge/M%26E_Analytics-0369A1?style=flat-square)

**Applied data science:**  
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat-square&logo=keras&logoColor=white)
![KNN](https://img.shields.io/badge/KNN-7C3AED?style=flat-square)
![Arabic NLP](https://img.shields.io/badge/Arabic_NLP-4338CA?style=flat-square)
![Text mining](https://img.shields.io/badge/Text_mining-4338CA?style=flat-square)
![Model evaluation](https://img.shields.io/badge/Model_evaluation-6366F1?style=flat-square)

---

## Education and certifications

- **Master of Business Administration**, Liverpool John Moores University, United Kingdom — ongoing
- **Bachelor of Engineering in Information Technology**, University of Aden, Yemen
- **Microsoft Data Architecture for Modern Data Stacks**, Coursera — 2026
- **MEAL DPro Flex Certification**, Humentum — 2020
- **Oracle Database Administration and Development certifications** — 2014

---

## Let’s connect

I am interested in analytics, data analysis, business intelligence, monitoring and evaluation, data quality, and applied analytical work where technical methods are connected to real operational or business questions.

[LinkedIn](https://www.linkedin.com/in/fadisaif) · [GitHub](https://github.com/FadiSaif-BA) · [Email](mailto:fadi.saif@outlook.com)

> Turning complex operational data into clearer analysis, more reliable evidence, and better-informed decisions.

