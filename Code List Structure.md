# Person Alert Codes: Structure and Formation

## Overview

The Person Alert Codes provide a structured and standardised way of recording alerts about individuals. Each code captures a specific category of risk, need, or condition, with subcodes detailing particular examples or conditions within that category.  

The codes were inspired by established standards and frameworks, including NHS/SNOMED for medical terminology, DWP for welfare-related alerts, SAVII for social care, and HACT for housing data standards.

## Code Structure

Each code follows a hierarchical format:


- **CATEGORYCODE** – Represents the broad category of the alert.  
- **SUBCODE** – Represents a specific example or condition within that category.  

# Person Alert Codes: Structure and Purpose

## Overview

The `person_alert_codes` table is designed to standardise alerts about individuals for housing and social care purposes. Each code provides both a **broad category** and a **specific subcode**, allowing staff to quickly understand the nature of a person's condition, risk, or need.

The codes are organised into main categories:

| Code  | Description         |
|-------|-------------------|
| MED   | Medical            |
| PREG  | Pregnancy          |
| MH    | Mental Health      |
| AGE   | Age Group          |
| RISK  | Risk               |
| SAF   | Safeguarding       |
| COMM  | Communication      |

## Table Structure

The `person_alert_codes` table contains the following fields:

| Field Name           | Type        | Description |
|----------------------|------------|-------------|
| `person_alert_code_id` | INTEGER    | Unique internal ID for the record. |
| `alert_code`          | VARCHAR(10) | Top-level code representing the category (e.g., `MED1`). |
| `alert_subcode`       | VARCHAR(15) | Subcode for specific conditions (e.g., `MED1.01`). |
| `alert_category_id`   | INTEGER     | Foreign key linking to `alert_categories`. |
| `alert_name`          | VARCHAR(50)| Name of the general condition or risk type (e.g., "Respiratory Condition"). |
| `alert_subname`       | VARCHAR(50)| Specific condition or example within the category (e.g., "Asthma"). |
| `is_critical`         | BOOLEAN     | Marks if the condition requires urgent attention. |
| `is_awaab_relevant`   | BOOLEAN     | Marks if the condition is relevant to Awaab’s Law (housing hazards). |
| `repairs_impact`      | VARCHAR(10) | Indicates how repairs impact the person (`High`, `Medium`, `Low`, `None`). |
| `support_required`    | TEXT        | Notes on additional support needed (e.g., "Use interpreter", "Prioritise mould/damp repairs"). |

## How Codes Are Formed

- **Category + Subcode**: Each main category has a prefix (`MED`, `MH`, etc.) followed by a number for the subcategory (`1`, `2`, …). Specific conditions use a dot notation (e.g., `MED1.01` for Asthma).  
- **Alert Name**: Represents the general type of condition (e.g., "Respiratory Condition").  
- **Alert Subname**: Provides the precise condition or risk example (e.g., "Asthma").  
- **Criticality & Relevance**: Flags help prioritise support and link to housing compliance (e.g., Awaab’s Law).  
- **Repairs Impact & Support Required**: Guidance for housing staff to tailor interventions and ensure safety and wellbeing.  

## Examples

### Respiratory Conditions

| alert_code | alert_subcode | alert_name          | alert_subname       | is_critical | is_awaab_relevant | repairs_impact | support_required |
|------------|---------------|-------------------|-------------------|------------|-----------------|----------------|-----------------|
| MED1       | MED1.01       | Respiratory Condition | Asthma             | TRUE       | TRUE            | High           | Prioritise mould/damp repairs |
| MED1       | MED1.02       | Respiratory Condition | COPD/Chronic Lung Disease | TRUE | TRUE | High | Ensure adequate heating/ventilation |
| MED1       | MED1.03       | Respiratory Condition | Bronchiectasis      | TRUE       | TRUE            | High           | Ensure access to emergency services |

### Cardiovascular Conditions

| alert_code | alert_subcode | alert_name             | alert_subname                  | is_critical | is_awaab_relevant | repairs_impact | support_required |
|------------|---------------|----------------------|--------------------------------|------------|-----------------|----------------|-----------------|
| MED2       | MED2.01       | Cardiovascular Condition | Hypertension (High Blood Pressure) | FALSE | FALSE           | Medium         | Provide stress-free environment; ensure regular medical access |
| MED2       | MED2.02       | Cardiovascular Condition | Heart Disease                  | TRUE       | TRUE             | High           | Avoid upper floors without lift; ensure emergency access routes |
| MED2       | MED2.05       | Cardiovascular Condition | Arrhythmia                     | TRUE       | TRUE             | High           | Enable rapid emergency response; avoid isolated accommodation |

> These examples illustrate how the combination of category, subcode, and supporting fields provides both **structured data** for reporting and **actionable guidance** for staff.  



## Key Points

- **Categories** group related conditions for easier management and reporting.  
- **Subcodes** provide specificity for individual conditions or scenarios.  
- Codes are designed to be **clear, actionable, and interoperable** across housing management and related systems.  
- The hierarchy supports both **broad reporting** (category-level) and **detailed case management** (subcode-level).

- ---

---

## Disclaimer

This is the **first draft** of the development of the Person Alert Codes system. The structure, categories, and examples provided here are preliminary and may evolve as we receive feedback and practical insights from users.  

We welcome suggestions, corrections, and contributions from the community to help improve and refine these codes for safer, more effective, and standardised use across housing and care settings.

