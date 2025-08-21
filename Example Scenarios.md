# Person Alert Codes Examples

## Demonstrating the Value of the Person Alert Model

These examples illustrate how the **Person Alert data model** supports both tenants and housing providers by ensuring that critical health, safety, and vulnerability information is captured, tracked, and acted upon effectively.  

By linking predefined alert codes to tenant records, the model allows housing providers to:

* **Prioritise support**: Critical medical or age-related alerts help staff identify tenants who require urgent attention.  
* **Ensure safety**: Alerts related to environmental risks—such as asthma triggers or oxygen use—enable contractors and maintenance teams to take precautions before entering a property.  
* **Track progress over time**: Changes in a tenant’s health or living conditions can be logged in `person_alert_history`, providing a clear audit trail for interventions.  
* **Coordinate actions across teams**: Linking alerts to maintenance, repairs, or health services ensures that interventions address both health and environmental risks.  
* **Demonstrate compliance and due diligence**: By recording Awaab-relevant alerts and critical conditions, housing providers can show proactive management of tenant safety in line with regulatory expectations.  

These examples, covering a child with asthma and a tenant using oxygen at home, show how the model creates **a single, structured framework** to manage diverse risks, improve tenant wellbeing, and reduce potential hazards in social housing.

---

# 1. Example of a Medical Alert: Child with Asthma

This example shows how our data model helps you record and respond to medical alerts for tenants, ensuring that those with health vulnerabilities receive timely support.

Explore more guidance on [managing tenant health risks](https://www.gov.uk/government/publications/managing-health-risks-in-social-housing).

## Example

A 10-year-old child living in a social housing property has been diagnosed with asthma. The GP has reported that the child’s condition is currently unstable due to frequent wheezing and night-time coughing.  

The child’s parents have noted that poor ventilation and damp conditions in the bedroom seem to trigger asthma attacks. The child has been prescribed an inhaler, and the GP has recommended monitoring indoor air quality and addressing environmental triggers.

## Linked Alert Codes

1. **Medical Condition**: `MED2.01` – Asthma / Chronic Respiratory Condition  
2. **Age Vulnerability**: `AGE1.05` – School-age child (6–12 years)

> Both alerts are linked in the `person_alert` table, ensuring:
>
> * The child’s underlying medical condition is recorded (Medical / Respiratory)  
> * Age-related vulnerability is captured, highlighting need for supervision and safe environment  
> * Alerts are tracked long-term and changes logged in `person_alert_history`  
> * Criticality and Awaab’s Law relevance are properly recorded

### How the model supports action

The alerts are **critical** because:

* Asthma makes the child vulnerable to environmental triggers (e.g., damp, dust, poor ventilation).  
* School-age children require safe living and study spaces, including monitoring indoor air quality.

Housing providers can:

* Flag the property record for priority follow-up.  
* Log support actions, such as liaising with the GP, improving ventilation, or addressing damp.  
* Track progress over time to ensure interventions are effective.  
* Coordinate with maintenance or housing teams to reduce environmental triggers.

### Data Mapping in the Model

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 12345 | Tenant ID |
| `person_alert_code_id` | MED2.01 | Links to Medical Condition (Asthma) |
| `alert_category_id` | 1 | 1 = Medical|
| `is_critical` | true | health |
| `is_awaab_relevant` | true  | True for Asthma (linked to housing conditions) |
| `alert_progress` | Deteriorating | Updated as condition changes |
| `support_required` | Contact GP, improve ventilation| Actionable guidance for staff |

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 12345 | Tenant ID |
| `person_alert_code_id` | AGE1.05 | Links to Age Vulnerability (School-age child) |
| `alert_category_id` | 4 | Age |
| `is_critical` | true | age vulnerability |
| `is_awaab_relevant` | false | True for Asthma (linked to housing conditions), false for Age |
| `alert_progress` | Deteriorating | Updated as condition changes |
| `support_required` | Contact GP, improve ventilation, ensure safe home environment and study space | Actionable guidance for staff |

---

# 2. Example of a Medical Alert: Elderly Tenant at Risk of Falls

This example shows how our data model helps you record and respond to alerts for tenants at risk of falling, ensuring preventative measures are put in place to reduce harm.

## Example

An 82-year-old tenant lives alone in a first-floor flat with no lift access.  
The tenant’s GP reports that she has poor balance due to osteoarthritis and has fallen twice in the past year.  

The tenant’s daughter has raised concerns that clutter in the hallway and poor lighting on the communal stairs make the risk of falling much higher.

> This maps to the **person_alert** table of our data model, allowing you to:
>
> * record tenant ID, alert creation date, and source organisation (GP)  
> * link to a predefined alert code in `person_alert_codes` (e.g., MED7.04 - "Osteoarthritis")  
> * categorise the alert using `alert_categories` (**Medical**)  
> * update the `alert_progress` field as interventions are put in place  
> * store history in `person_alert_history` for transparency

### How the model supports action

The alert is flagged as **critical** because falls could lead to hospitalisation or worse.

The housing provider can:

* Arrange a home safety assessment.  
* Install additional handrails and improve stair lighting.  
* Work with the tenant’s family to reduce clutter and hazards.  

### Data Mapping in the Model

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 67890 | Tenant ID |
| `person_alert_code_id` | MED7.04 | Links to `person_alert_codes` |
| `alert_category_id` | MED7 | Medical |
| `is_critical` | true | Urgent safety risk |
| `is_awaab_relevant` | false | Not related to Awaab’s Law |
| `alert_progress` | Stable | Updated after safety improvements |
| `support_required` | Prioritise mobility adaptations and non-slip surfaces | Actions to reduce risk

---

# 3. Example of a Mental Health Alert: Tenant with Severe Depression and Risk of Self-Harm

This example shows how our data model helps you record and respond to multiple related mental health alerts for the same person, ensuring sensitive and appropriate support.

## Example

A 35-year-old tenant has disclosed to a housing officer that she is experiencing severe depression and has had recent thoughts of self-harm.

Her GP has confirmed that she is receiving treatment and referred her to a community mental health team.  
The housing officer notes that the tenant has been missing rent payments and avoiding social contact.

Because there are **two distinct but related risks** — depression and self-harm — the system records **two linked alert codes** in `person_alert_codes`:

- `MH1.03` - 'Depression (Severe or Recurrent)' – for severe depression  
- `MH1.06` - 'Self-harm' – for self-harm ideation or behaviour

> This maps to the **person_alert** table of our data model by:
>
> * creating one `person_alert` record for each code, both linked to the same tenant  
> * categorising each alert as **Mental Health** in `alert_categories`  
> * tracking changes in `alert_progress` independently for each alert  
> * storing all updates in `person_alert_history` to keep an accurate and auditable record

### How the model supports action

Both alerts are marked as **critical** due to the high level of personal risk.

The housing provider can:

* Flag the account for sensitive handling by customer service staff.  
* Schedule regular well-being check-ins with the tenant.  
* Liaise with the tenant’s GP and mental health team (with consent).  
* Record separate notes and progress updates for each alert code.

### Data Mapping in the Model

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 34567 | Tenant ID |
| `person_alert_code_id` | `MH1.03` | Links to `person_alert_codes` |
| `alert_category_id` | MH1 | Mental Health |
| `is_critical` | true | Risk of harm |
| `alert_progress` | Improving | For depression condition |
| `support_required` | Well-being checks, sensitive handling | Actions for staff |

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 34567 | Tenant ID (same as above) |
| `person_alert_code_id` | `MH1.06` | Links to `person_alert_codes` |
| `alert_category_id` | MH1 | Mental Health |
| `is_critical` | true | Risk of self-harm |
| `alert_progress` | Stable | For self-harm risk |
| `support_required` | Crisis support plan, close monitoring | Actions for staff

---

By recording **two separate alerts** for the same person, the model allows:

* Different progress tracking for each condition.  
* Targeted interventions that address each risk appropriately.  
* Clear auditing of how each issue was managed over time.

---

# 4. Example of a Medical and Safety Alert: Oxygen Use in the Home

This example demonstrates how our data model captures both medical vulnerability and practical safety risks, ensuring staff and contractors are fully informed.

## Example

A tenant has **chronic obstructive pulmonary disease (COPD)** and uses a **home oxygen concentrator** indefinitely.  
The oxygen supplier has notified the housing provider of the equipment, which presents a fire hazard if contractors work with heat, sparks, or open flames.

## Linked Alert Codes

1. **Medical Condition**: `MED1.02` – COPD / Chronic Lung Disease  
2. **Safety Risk**: `RISK5.01` – Oxygen Equipment Risk

> Both alerts are linked in the `person_alert` table, ensuring:
>
> * The tenant’s underlying condition is recorded (Medical / Respiratory)  
> * The safety risk is highlighted to all staff and contractors  
> * Alerts are tracked long-term and changes logged in `person_alert_history`  
> * Criticality and Awaab’s Law relevance are properly recorded

### How the model supports action

The alerts are **critical** because:

* COPD makes the tenant vulnerable to poor air quality (Awaab’s Law relevant).  
* Oxygen is highly flammable, posing a fire hazard to anyone in the home.

Housing providers can:

* Flag the property record so contractors are automatically informed.  
* Update fire and health risk assessments.  
* Work with the tenant to ensure safe storage and use of oxygen equipment.  
* Coordinate emergency procedures if needed.

### Data Mapping in the Model

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 11223 | Tenant ID |
| `person_alert_code_id` | MED1.02 | Links to Medical Condition (COPD) |
| `alert_category_id` | 1 | Medical |
| `is_critical` | true | Both alerts critical: health + fire hazard |
| `is_awaab_relevant` | true / false | Medical = true, Safety Risk = false |
| `alert_progress` | Stable | Ongoing condition and equipment in use |
| `support_required` | Fire safety checks, contractor alerts, ventilation advice | Actions to ensure tenant safety |

| Field | Example Value | Notes |
|-------|---------------|-------|
| `person_id` | 11223 | Tenant ID |
| `person_alert_code_id` | RISK5.01 | Links to Safety Risk (Oxygen Equipment) |
| `alert_category_id` | 5 | RISK |
| `is_critical` | true | fire hazard |
| `is_awaab_relevant` |false | false |
| `alert_progress` | Stable | Ongoing condition and equipment in use |
| `support_required` | Fire safety checks, contractor alerts | Actions to ensure tenant safety |


