# How the Model Works – Data Flow

The system is designed to track alerts related to tenants in a structured and consistent way. Below is a step-by-step explanation of how the data flows.

---

## 1. Creating an Alert
When an event occurs that requires monitoring, such as a doctor (GP) identifying a tenant with a medical condition, the alert is recorded in the `person_alert` table.  

This record links to several key pieces of information:

- **Person**: The tenant affected.
- **Organisation**: The source of the alert (e.g., a specific GP practice, Hospital, Council).
- **Source Type**: How the alert was generated (e.g., GP, Hospital, Social Worker).
- **Alert Code**: A predefined code from `person_alert_codes` that categorises the alert.
- **Alert Category**: The broader category of the alert from `alert_categories` (e.g., Medical, Safeguarding, Age).

---

## 2. Tracking Changes
Alerts are dynamic. For example, if the tenant’s condition improves or worsens, the `alert_progress` field is updated to reflect this change.

Every change is automatically logged in `person_alert_history` to create a clear audit trail. This ensures transparency and accountability.

---

## 3. Closing Alerts
Once an alert is no longer relevant (for instance, the medical issue is resolved), it can be closed by entering an `end_date`.

Even after closure, the history of the alert remains accessible for reporting and analysis.

---

## 4. Benefits of the Structured Model
- **Consistency**: Every alert follows the same format and structure.
- **Traceability**: Changes are fully auditable through the history table.
- **Analytics**: Data can be analysed to identify trends, risks, and operational insights across tenants and organisations.

---

## 5. Handling Special Category Data

Some alerts involve data that is considered particularly sensitive under ICO guidance (e.g., health conditions, ethnicity, religion).  
These are flagged using the `special_category_data_types` table.  

This ensures that housing providers are aware when alerts contain special category information, so they can apply the correct safeguards, access controls, and handling procedures.

---

## 6. Data Flow Diagram

```mermaid
flowchart LR
    Person["Person (Tenant)"] --> PA[person_alert]
    Organisation["Organisation (e.g., GP)"] --> PA
    PA --> PAC[person_alert_codes]
    PAC --> AC[alert_categories]
    PA --> ST[source_types]
    PA --> PAH[person_alert_history]
    PA --> SCDT[special_category_data_types]

    style PA fill:#f9f,stroke:#333,stroke-width:2px
    style PAC fill:#bbf,stroke:#333,stroke-width:2px
    style AC fill:#bfb,stroke:#333,stroke-width:2px
    style ST fill:#bbf,stroke:#333,stroke-width:2px
    style PAH fill:#fbf,stroke:#333,stroke-width:2px
    style SCDT fill:#fbb,stroke:#333,stroke-width:2px





