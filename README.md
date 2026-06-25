# SeeSkill-PH

**A Data-Driven Competency Mapping and Skill Prioritization Framework for Data and AI Roles in the Philippine Labor Market**

SeeSkill-PH transforms job postings into a structured skill intelligence dashboard. The project uses a language model-assisted pipeline to extract hard technical skills from job descriptions, standardize overlapping skill terms, organize them into competency clusters, score their market relevance, and visualize the results in Power BI.

The project is designed to help learners, career shifters, and early-stage professionals understand which technical skills are commonly requested across Data, AI, and Software-related roles.

---

## Project Overview

Job descriptions often contain long and inconsistent lists of required skills. Similar skills may appear under different names, broad terms may be mixed with specific tools, and soft skills may be listed alongside hard technical requirements.

SeeSkill-PH addresses this by converting unstructured job posting text into structured, dashboard-ready datasets. The project focuses only on hard, concrete, actionable, and portfolio-buildable skills.

Examples of target skills include:

```text
Python
SQL
Power BI
Tableau
AWS
Azure
Snowflake
Airflow
Machine Learning
RAG
LangChain
Computer Vision
Cybersecurity
React
Node.js
```

The final Power BI dashboard provides a market-level view of skill demand, role-skill alignment, competency clusters, and learning pathways.

---

## Dashboard Preview

### Market Overview

[Market Overview](assets/images/01_market_overview.png)

Summarizes the job market snapshot by role, seniority, salary range, and top skills.

### Competency Clusters

[Competency Clusters](assets/images/02_competency_clusters.png)

Shows high-level skill families, cluster demand, top skills per cluster, and cluster-level metrics.

### Role-Skill Matrix

[Role-Skill Matrix](assets/images/03_role_skill_matrix.png)

Compares competency and skill demand across the target role categories.

### Skill Tree / Learning Map

[Skill Tree](assets/images/04_skill_tree.png)

Displays one learning map per competency cluster. Skills are positioned based on learning level, difficulty, and demand priority.

### Skill Explorer

[Skill Explorer](assets/images/05_skill_explorer.png)

Provides a searchable table of final cleaned skills, clusters, categories, and scoring metrics.

---

## Key Features

* Extracts technical skills from raw job descriptions.
* Filters out soft skills, generic responsibilities, and non-portfolio-buildable phrases.
* Standardizes overlapping skill terms such as `Microsoft Power BI` into `Power BI`.
* Assigns each skill to one primary competency cluster.
* Classifies job postings into standardized role categories.
* Estimates seniority and experience levels for scoring.
* Scores skills based on demand, universality, accessibility, transition relevance, and experience barrier.
* Generates dashboard-ready CSV outputs.
* Visualizes skill demand and competency structure in Power BI.

---

## Target Role Categories

The dashboard groups job postings into the following role categories:

```text
AI/ML Engineer
Data Analyst / BI / Scientist
Data Engineer
Full-Stack Developer
Other/Adjacent
```

These role categories are used to compare skill demand across different job families.

---

## Competency Clusters

Extracted skills are grouped into one primary competency cluster. Example clusters include:

```text
Agentic AI
Generative AI
RAG and Vector Search
BI and Visualization
Data Engineering Pipelines
Cloud Platforms
Cloud Data Services
Cybersecurity
Computer Vision
Information Systems
Web Development
MLOps and Deployment
Databases and Querying
Programming Languages
```

The cluster structure allows the dashboard to show both detailed skills and broader competency areas.

---

## Processing Workflow

The project follows a multi-pass processing pipeline.

### 1. Raw Data Loading

The input dataset contains job postings collected from publicly accessible job boards. Each row represents one job posting and includes fields such as job title, company, location, salary when available, work setup, and raw job description.

### 2. Initial Skill Extraction

A language model extracts candidate hard skills from each job description. At this stage, the extracted skills may still contain duplicates, aliases, or overly specific wording.

### 3. Skill Synthesis and Standardization

Candidate skills are cleaned and standardized. Similar skill phrases are merged into a single canonical skill name.

Examples:

```text
Python Programming → Python
Microsoft Power BI → Power BI
MS Excel → Excel
Apache Airflow → Airflow
```

Grouped skill phrases are split when needed.

Example:

```text
Python, SQL, AWS → Python | SQL | AWS
```

### 4. Skill Filtering

The pipeline removes soft skills and generic job responsibilities.

Examples of removed terms:

```text
team player
communication skills
works under pressure
stakeholder management
training junior members
```

The goal is to retain only skills that can be learned, practiced, certified in, or turned into a portfolio project.

### 5. Competency Clustering

Each cleaned skill is assigned to one primary competency cluster. The cluster assignment is used for dashboard grouping, skill cards, role comparison, and skill-tree construction.

### 6. Job Enrichment

Job postings are classified into standardized role categories. Seniority and experience levels are also inferred from title, description, and available experience signals.

### 7. Skill and Cluster Scoring

Skills and clusters are scored using normalized metrics such as:

```text
Demand Score
Universality Score
Entry Accessibility Score
Transition Priority Score
Experience Barrier Score
```

These scores are used to prioritize skills in the dashboard and support the skill explorer and learning map.

### 8. Dashboard Export

The processed tables are exported as CSV files and loaded into Power BI for visualization.

---

## How to Run

1. Open the data processing notebook in Google Colab.
2. Mount Google Drive or update the input path to the job posting dataset.
3. Run the notebook from top to bottom.
4. Export the processed CSV files.
5. Open the Power BI dashboard file.
6. Load or refresh the processed CSV files.
7. Review the dashboard pages and visuals.

---

## Notes

The dataset was created from publicly accessible job postings. The project represents a job market snapshot and should be interpreted as an exploratory skill intelligence tool rather than a complete labor market census.

The language model pipeline is used to assist with extraction, standardization, and clustering, but the outputs may still require review when extending the dataset or adapting the project to a new job market.
