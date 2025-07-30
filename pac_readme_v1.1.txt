# Person Alert Code Standard

**Proposed Sector-Wide Standard for Housing Providers**  
Aligned with HACT Housing Data Standards  
**Version:** Draft v1.0  
**Author:** Elena Iurco  
**Date:** 30 July 2025

---

## Overview

This repository contains the **Person Alert Code Standard** — a proposed sector-wide data model and design documentation aimed at social housing providers across the UK. The standard supports consistent capture, management, and sharing of alerts related to tenants’ health, risks, and support needs.

The model aligns with HACT Housing Data Standards and emerging regulatory frameworks such as Awaab’s Law, helping housing providers safeguard vulnerable tenants and make better operational decisions.

---

## Contents

| File / Folder           | Description                                                       |
|------------------------|-------------------------------------------------------------------|
| `erd/`                 | Entity Relationship Diagrams (ERD) illustrating the data model   |
| `dbml/`                | DBML files defining table structures and relationships            |
| `sql/schema.sql`       | SQL DDL scripts to create database tables and constraints         |
| `docs/guidance.md`     | Implementation guidance and best practices                        |
| `docs/design-decisions.md` | Rationale and detailed explanations of design choices          |
| `examples/`            | Sample data, example queries, and use case demonstrations         |
| `README.md`            | This document                                                     |

---

## Data Tables

### `person_alert_codes`

Defines the standardised alert codes used to classify various tenant alerts such as medical conditions, risk factors, or environmental sensitivities.

| Field              | Description                                                      |
|--------------------|------------------------------------------------------------------|
| `alert_code_id`     | Unique internal identifier for the alert code                    |
| `alert_code`        | Top-level grouping code (e.g. MED1)                             |
| `alert_subcode`     | Detailed subcode (e.g. MED1.01)                                 |
| `alert_category`    | Broad classification (e.g. Medical, Risk, Environmental)        |
| `alert_name`        | Group name (e.g. Respiratory Condition)                         |
| `alert_subname`     | Specific condition or risk (e.g. Asthma)                        |
| `is_critical`       | Boolean flag for life-critical alerts                           |
| `is_awaab_relevant` | Boolean flag indicating relevance to Awaab’s Law               |
| `repairs_impact`    | Impact level on repairs: High, Medium, Low, None                |
| `support_required`  | Optional instructions (e.g. Use interpreter, Extra checks)     |

---

### `person_alert`

Stores individual tenant alert instances linked to persons and alert codes.

| Field               | Description                                                    |
|---------------------|----------------------------------------------------------------|
| `person_alert_id`    | Primary key                                                   |
| `person_id`          | Foreign key to tenant/person table                            |
| `alert_code_id`      | Foreign key to `person_alert_codes`                           |
| `alert_description`  | Free text notes or additional details (optional)             |
| `alert_source`       | Origin of alert (e.g. NHS, GP, Social Worker)                 |
| `created_by`         | Name or ID of the creator of this alert record                |
| `source_description` | Specific person or agency source detail                       |
| `informed_resident`  | Boolean indicating if resident was informed                   |
| `alert_progress`     | Enum: Stable, Improving, Deteriorating, Fluctuating, Unknown |
| `alert_duration_type`| Enum: Long Term, Temporary, Unknown                           |
| `alert_duration`     | Duration in days (optional)                                   |
| `start_date`         | Date when alert started                                       |
| `end_date`           | Date when alert ended (optional)                              |
| `review_date`        | Next review date (optional)                                  |
| `active`             | Boolean flag for current active status                        |
| `last_updated`       | Timestamp of last update                                     |
| `updated_by`         | User or system who last updated                              |

---

### `person_alert_history`

Logs all changes and updates made to `person_alert` records for audit and traceability.

| Field              | Description                                |
|--------------------|--------------------------------------------|
| `history_id`       | Primary key                                |
| `person_alert_id`  | Foreign key to the alert record            |
| `change_timestamp` | When the change was made                    |
| `changed_by`       | Who made the change                         |
| `change_type`      | Type of change (Created, Updated, Deleted)|
| `change_details`   | JSON or text description of the change     |

---

### `source_types`

Lookup table defining valid sources of alerts.

| Field          | Description                 |
|----------------|-----------------------------|
| `source_type_id`| Primary key                 |
| `source_name`   | Name of the source (e.g. NHS, GP, Self-Reported) |

---

### `alert_categories`

Lookup table for alert category types.

| Field              | Description                   |
|--------------------|-------------------------------|
| `alert_category_id` | Primary key                  |
| `category_name`     | Name of the category (e.g. Medical, Risk, Environmental) |

---

## Features & Principles

- **Sector Alignment:** Developed in accordance with HACT Housing Data Standards and MHCLG guidance.
- **Flexibility & Standardisation:** Combines standard codes with free text fields for contextual nuance.
- **Awaab’s Law Compliance:** Flags alerts requiring urgent housing-related interventions.
- **Data Integrity:** Enforces referential integrity and audit trails via history tracking.
- **Extensibility:** Designed to accommodate future categories and additional metadata.

---

## Use Cases

- Identifying tenants with health vulnerabilities affected by housing conditions.
- Prioritising critical repairs for tenants with life-critical alerts.
- Managing safeguarding and behavioural risks for contractors.
- Recording temporary conditions such as pregnancy or post-surgery recovery.
- Facilitating communication needs and support provisions.

---

## Getting Started

### Prerequisites

- Relational database (PostgreSQL recommended)
- Tools to view DBML and ER diagrams (e.g., dbdiagram.io)
- Basic knowledge of SQL and data modelling

### Setup

1. Review ER diagrams in the `erd/` folder to understand relationships.
2. Use DBML files in the `dbml/` folder to generate visual schema or import into supported tools.
3. Apply SQL DDL scripts from `sql/schema.sql` to your database to create tables and constraints.
4. Consult `docs/guidance.md` for advice on implementation best practices.
5. Review `docs/design-decisions.md` to understand design rationale.

---

## Contribution

Contributions and feedback are welcomed! Please follow these steps:

1. Fork the repository  
2. Make your changes or additions  
3. Submit a pull request with a clear description  
4. Open issues for discussion or questions  

All contributions must respect data ethics, tenant privacy, and regulatory compliance.

---

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use and adapt with attribution.

---

## Acknowledgements

This work is inspired by and builds upon:

- HACT Housing Data Standards  
- NHS clinical condition classifications  
- Sector collaboration on Awaab’s Law compliance  

---

If you would like, I can also help generate a `CONTRIBUTING.md` or `LICENSE` file for you. Just let me know!
