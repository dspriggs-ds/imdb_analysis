# 🎬 IMDb Data Analysis with Python and Box Office Mojo API

This project creates a clean, enriched dataset for analyzing movies and TV shows using publicly available IMDb data and box office revenue information.

## 📚 Overview

The dataset combines structured metadata from the [IMDb Datasets](https://datasets.imdbws.com/) with financial data retrieved via the [`boxoffice_api`](https://pypi.org/project/boxoffice-api/) Python package. The goal is to enable powerful insights into trends in ratings, revenue, genres, and release strategies.

## 📦 Data Sources

### 1. IMDb Official Datasets
- **URL:** [https://datasets.imdbws.com/](https://datasets.imdbws.com/)
- **Included Files:**
  - `title.basics.tsv.gz`: Title metadata (genres, release year, etc.)
  - `title.ratings.tsv.gz`: IMDb average rating and vote count
  - `title.crew.tsv.gz`: Directors and writers
  - `title.principals.tsv.gz`: Cast and crew by role

These files are extracted, cleaned, and transformed into Spark DataFrames.

### 2. Box Office Mojo API via `boxoffice_api`
- Retrieves up-to-date box office data:
  - Domestic/international gross revenue
  - Opening weekend performance
  - Distributor and studio metadata

## 🛠️ Dataset Creation Workflow

```mermaid
graph LR
  A[Download IMDb .tsv.gz Files] --> B[Parse with PySpark]
  B --> C[Filter: Movies, Non-null Ratings]
  C --> D[Enrich with boxoffice_api]
  D --> E[Merge on Title/Year]
  E --> F[Write Clean Dataset to Delta/Parquet]
````

### Key Steps

* Download and extract IMDb `.tsv.gz` files
* Transform raw data using PySpark
* Filter for movies with complete metadata and ratings
* Use `boxoffice_api` to enrich with financial performance
* Merge datasets to create a unified movie analytics dataset

## ✅ Use Cases

* Rating vs Revenue correlation analysis
* Genre performance trends
* Studio-based performance benchmarking
* Release strategy impact (e.g., opening weekend vs total gross)

## 📂 Output Format

The final dataset is stored in:

* Delta Lake format (for use in Databricks/Spark)
* OR Parquet format (for easy use in Pandas or other BI tools)

## ⚠️ Legal Notice

Use of IMDb data is subject to [IMDb's Terms of Use](https://www.imdb.com/conditions). This project is for educational and analytical purposes only.

---

## 🧠 Author

**David Spriggs**
[LinkedIn](https://www.linkedin.com/in/davidspriggs) • [GitHub](https://github.com/dspriggs-ds)


