# Country GDP Data ETL Pipeline

An automated Python ETL (Extract, Transform, Load) pipeline that extracts global Gross Domestic Product (GDP) data from IMF evaluations, transforms and normalizes numerical values, and exports structured datasets into JSON format and an SQLite database.

## Technical Overview & Architecture

This pipeline automates biannual financial reporting workflows by orchestrating four main stages:

1. **Extraction:** Scrapes GDP evaluation tables from web archives using `requests` and parses relevant attributes via `BeautifulSoup` into a Pandas DataFrame.
2. **Transformation:** Converts GDP string figures into floating-point numbers in billions of USD, rounds figures to two decimal places, and filters missing values.
3. **Loading:** Dual-persists structured data into a flat file (`Countries_by_GDP.json`) and a relational table (`Countries_by_GDP`) within an SQLite database (`World_Economies.db`).
4. **Validation & Auditing:** Queries the SQLite database to display high-value economies exceeding $100 Billion USD and logs pipeline stage execution timestamps to `etl_project_log.txt`.

---

## Tech Stack & Dependencies

* **Language:** Python 3.x
* **Libraries:**
  * `pandas` — DataFrame manipulation and data export (JSON/SQL)
  * `beautifulsoup4` — Web page HTML parsing
  * `requests` — HTTP request handling
  * `numpy` — Numerical operations and rounding
  * `sqlite3` — Relational database connection and query execution
  * `datetime` — Log event timestamping

---

## Repository Structure

```text
├── etl_project_gdp.py        # Main ETL execution script
├── Countries_by_GDP.json     # Output: Processed dataset in JSON format
├── World_Economies.db        # Output: SQLite database storing 'Countries_by_GDP' table
├── etl_project_log.txt       # Output: Timestamped pipeline execution log
└── README.md                 # Project documentation
