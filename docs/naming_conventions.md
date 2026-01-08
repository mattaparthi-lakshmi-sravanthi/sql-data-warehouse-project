# Naming Conventions

This document outlines the naming conventions used for schemas, tables, views, columns, and other objects in the data warehouse.

---

## Table of Contents

- General Principles  
- Table Naming Conventions  
  - Bronze Rules  
  - Silver Rules  
  - Gold Rules  
  - Glossary of Category Patterns  
- Column Naming Conventions  
  - Surrogate Keys  
  - Technical Columns  
- Stored Procedure Naming  

---

## General Principles

- **Naming Convention:** Use `snake_case` with lowercase letters and underscores (`_`) to separate words.  
- **Language:** Use **English** for all names.  
- **Avoid Reserved Words:** Do not use SQL reserved keywords as object names.  
- **Clarity:** Names must be meaningful, clear, and business-aligned.

---

## Table Naming Conventions

### Bronze Rules

All names must start with the **source system name**, and table names must match their original names **without renaming**.

**Pattern:**
```

<sourcesystem>_<entity>

```

- `<sourcesystem>`: Name of the source system (e.g., crm, erp)  
- `<entity>`: Exact table name from the source system  

**Example:**
```

crm_customer_info

```
Customer information from the CRM system.

---

### Silver Rules

All names must start with the **source system name**, and table names must match their original names **without renaming**.

**Pattern:**
```

<sourcesystem>_<entity>

```

- `<sourcesystem>`: Name of the source system (e.g., crm, erp)  
- `<entity>`: Exact table name from the source system  

**Example:**
```

crm_customer_info

```
Cleaned and transformed customer information from the CRM system.

---

### Gold Rules

All names must use **meaningful, business-aligned names**, starting with the **category prefix**.

**Pattern:**
```

<category>_<entity>

```

- `<category>`: Role of the table (e.g., dim, fact)  
- `<entity>`: Business-friendly name (e.g., customers, products, sales)  

**Examples:**
```

dim_customers
fact_sales

```

---

### Glossary of Category Patterns

| Pattern   | Meaning          | Example(s)                    |
|----------|------------------|-------------------------------|
| dim_     | Dimension table  | dim_customer, dim_product     |
| fact_    | Fact table       | fact_sales                    |
| report_  | Report table     | report_customers, report_sales_monthly |

---

## Column Naming Conventions

### Surrogate Keys

All primary keys in **dimension tables** must use the suffix `_key`.

**Pattern:**
```

<table_name>_key

```

- `<table_name>`: Name of the table or entity  
- `_key`: Indicates a surrogate key  

**Example:**
```

customer_key

```
Surrogate key in the dim_customers table.

---

### Technical Columns

All technical columns must start with the prefix `dwh_`.

**Pattern:**
```

dwh_<column_name>

```

- `dwh_`: Reserved for system-generated metadata  
- `<column_name>`: Describes the column’s purpose  

**Example:**
```

dwh_load_date

```
Stores the date when the record was loaded into the data warehouse.

---

## Stored Procedure Naming

All stored procedures used for loading data must follow this pattern:

**Pattern:**
```

load_<layer>

```

- `<layer>`: bronze, silver, or gold  

**Examples:**
```

load_bronze
load_silver
load_gold

```

---

## Example Summary

| Object Type      | Example Name        |
|------------------|---------------------|
| Bronze Table     | crm_customer_info   |
| Silver Table     | crm_customer_info   |
| Gold Dimension   | dim_customers       |
| Gold Fact        | fact_sales          |
| Surrogate Key    | customer_key        |
| Technical Column | dwh_load_date       |
| Stored Procedure | load_silver         |

---

**End of Document**
