# Healthcare Metrics Project

## Project Overview
**Objective**: Build a Data Engineering/Analytics pipeline using healthcare CSV files, calculate key metrics, and present insights via an interactive dashboard.

---

## Repository Structure


---

## Steps & Deliverables

### Step 2: Initial Data Analysis (`01_exploratory_data.ipynb`)
**Objective**: Analyze raw data for schema, relationships, and data quality.  
**Tasks**:
- Schema exploration and column relationships.
- Missing value analysis (e.g., histograms, summary tables).
- Duplicate detection and outlier identification.
- Basic visualizations (e.g., distributions, correlations).  
**Tools**: Pandas, NumPy, Matplotlib/Seaborn.  
**Deliverables**:
- Report on data quality (missing values, duplicates).
- List of key columns for joins (e.g., `CMS Certification Number (CCN)`).

---

### Step 3: Pipeline Architecture (`02_aws_glue_formation.ipynb`)
**Objective**: Design and document a scalable data pipeline.  
**Tasks**:
- Create architecture diagrams (Lucidchart) for ingestion, transformation, and storage.
- Define AWS Glue workflows for ETL.
- Document approval from SMEs.  
**Deliverables**:
- Pipeline architecture diagram (ingestion → transformation → Snowflake).
- Solution design document (tools, workflows, assumptions).

---

### Steps 4-6: Data Pipeline & Metrics (`04_healthcare_rpt_matrics.ipynb`)
**Objective**: Build pipeline, calculate metrics, and create a dashboard.  
**Tasks**:
1. **Pipeline Implementation**:
   - Ingest raw CSV files.
   - Clean, validate, and transform data.
   - Load into Snowflake.  
2. **Calculate Metrics**:
   - **Staffing**: Nurse-to-patient ratio, overtime %, shifts per nurse.
   - **Facility**: Occupancy rates, bed utilization, patient throughput.
   - **Quality**: Readmission rates, ALOS, satisfaction scores.
   - **Cost**: Payroll costs, cost per patient stay.
   - **Operational**: Shift utilization, staff attrition trends.  
3. **Dashboard**:
   - Interactive visualizations (Plotly/Dash).
   - Filters for state, hospital, and time.  
**Deliverables**:
- Working pipeline code (Python/SQL).
- Metrics calculations (Pandas).
- Dashboard with heatmaps, trend lines, and bar charts.

---

### Step 7: Submission & Review
**Deliverables**:
- Pipeline documentation (dbt for data lineage).
- Data dictionary (`NH_Data_Dictionary.pdf`).
- Dashboard video/presentation explaining design choices.  
**Tech Stack Justification**:
- **AWS Glue**: Serverless ETL for scalability.
- **Snowflake**: Cloud data warehousing for performance.
- **Plotly/Dash**: Interactive visualizations.
- **dbt**: Data transformation and lineage tracking.

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Healthcare-Metrics-Project.git# Healthcare-Metrics-Project
**Objective:** Build a Data Engineering/Analytics pipeline using provided healthcare CSV files, calculate key metrics, and present insights via a dashboard.
