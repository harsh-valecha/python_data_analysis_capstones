<div align="center">

# Python Data Analysis Capstones

### Practical data workflows with pandas, Jupyter, Excel, JSON, and SQLite

<p>
	A collection of focused projects for loading, exploring, transforming, filtering,
	sorting, and exporting structured data in Python.
</p>

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-Data%20Analysis-150458?style=flat-square&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-2E7D32?style=flat-square)

</div>

## Overview

This repository brings together four practical capstone exercises that use common business data formats. Each notebook follows a clear workflow: load source data, inspect its structure, answer questions with Python, and save useful results for further use.

The projects demonstrate how the same analytical mindset transfers across flat files, spreadsheets, semi-structured JSON, and relational databases.

## Project Map

| Capstone | Data source | What it demonstrates | Key files |
| --- | --- | --- | --- |
| **Student Marks** | CSV | DataFrame exploration, filtering, sorting, and exporting transformed results | [Notebook](csv_capstone/students.ipynb) · [Source data](csv_capstone/student_marks.csv) |
| **Product Analysis** | Excel | Reading workbooks, inspecting product data, selecting categories, and exporting expensive products | [Notebook](excel_capstone/product.ipynb) · [Source data](excel_capstone/product_catalog.xlsx) |
| **Employee Records** | JSON | Loading nested records, transforming JSON data into tabular form, and querying employee information | [Notebook](json_capstone/employee.ipynb) · [Source data](json_capstone/employees.json) |
| **Organisation Database** | SQLite | Connecting to a database, inspecting tables, and using SQL queries to retrieve organisation data | [Notebook](sqlite_capstone/organisation.ipynb) · [Database](sqlite_capstone/organisation.db) |

## Skills Practised

- Reading and writing CSV, Excel, JSON, and SQLite data
- Exploring datasets with `pandas`
- Selecting rows and columns with expressive conditions
- Sorting and grouping tabular data
- Working with DataFrames and database results
- Exporting analysis outputs to reusable files
- Building repeatable notebook-based data workflows

## Repository Structure

```text
.
├── csv_capstone/
│   ├── students.ipynb
│   ├── student_marks.csv
│   ├── student_sorted_df.csv
│   └── students_sorted_csv.csv
├── excel_capstone/
│   ├── product.ipynb
│   ├── product_catalog.xlsx
│   └── expensive_prod.xlsx
├── json_capstone/
│   ├── employee.ipynb
│   ├── employees.json
│   └── finance_json.json
├── sqlite_capstone/
│   ├── organisation.ipynb
│   └── organisation.db
├── requirements.txt
└── readme.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone <repository-url>
cd python_tdd
```

### 2. Create and activate a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### 4. Open the notebooks

```bash
jupyter notebook
```

Open any capstone notebook and run the cells from top to bottom. VS Code users can open the repository directly and run the notebooks with the Jupyter extension.

## Outputs

The analysis produces reusable files alongside the source data, including sorted student datasets and filtered Excel results. Keeping these outputs in each capstone folder makes the transformation from raw input to processed data easy to follow.

## Tools Used

| Tool | Purpose |
| --- | --- |
| **Python** | Core programming language |
| **Jupyter Notebook** | Interactive analysis and documentation |
| **pandas** | Data loading, transformation, and analysis |
| **openpyxl** | Excel workbook support |
| **SQLite** | Relational data storage and querying |

## Learning Focus

The project is designed as a practical foundation for data analysis. It focuses on writing readable steps, understanding how data is shaped in different storage formats, and producing results that can be inspected or reused outside the notebook.

---

<div align="center">

Built as a practical Python data analysis portfolio.

</div>
