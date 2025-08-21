# Person Alert Codes Repository

Welcome to the **Person Alert Codes** repository. An open source project in collaboration with MHCLG and HACT  for implementing standardised person alert codes within Social Housing. 

This project provides a standardised way of recording, managing, and sharing critical information about tenants’ personal circumstances, risks, and needs across housing organisations. By using these codes, housing providers can improve tenant safety, comply with regulatory requirements, and enable better coordination across teams.

This repository contains all the resources you need to understand, implement, and use the Person Alert Codes system.

---

## How to Navigate This Repository

This repository contains all the resources you need to understand, implement, and use **Person Alert Codes**. Here’s a simple guide to help you find what you need:

### 1. Overview and Guidance
- **[Introducing Person Alert Codes](./Introducing%20Person%20Alert%20Codes.md)** – High-level explanation of what the system is and why it matters.  
- **[Implement Person Alert Codes](./Implement%20Person%20Alert%20Codes.md)** – Step-by-step guidance for applying the codes in your housing organisation.  
- **[How the model works](./How%20the%20model%20works.md)** – Explains the code structure, hierarchy, and categories.

### 2. Code Structure and Examples
- **[Code List structure](./Code%20List%20structure.md)** – Shows how top-level codes (like `MED1`) and subcodes (`MED1.01`) are formed, with examples for medical, mental health, and other categories.  
- **[Example Scenarios](./Example%20Scenarios.md)** – Illustrates practical use cases in housing settings to help you understand when and how to use alerts.  
- **[Design Decisions](./Design%20Decisions.md)** – Details why certain fields exist, how criticality and support needs are recorded, and other design considerations.

### 3. Technical Files
These files are mostly for technical teams, but can be referenced for data understanding:
- **[person_alert.sql](./person_alert.sql)** – Contains the full SQL DDL for creating the alert tables.
- **[person_alert.json](./person_alert.json)** – JSON schema version of the table for integration with other systems.  
- **[person_alert.erd](./person_alert.erd)** – Entity-Relationship Diagram showing the connections between alerts, categories, and other entities.  
- **[person_alert.dblm](./person_alert.dblm)** – Database lifecycle model, showing how alert data is created, updated, and maintained over time.

### 4. Using the Tables
- Start with the **SQL or JSON tables** to understand what alerts exist and their structure.  
- Use **Code List structure** for examples on how to interpret top-level codes and subcodes.  
- Reference **Example Scenarios** to see how these codes guide decisions in housing operations.  

By following this path, housing teams can quickly understand the purpose, use, and technical structure of Person Alert Codes without needing deep technical knowledge.

---

### A Note on Development and Inspiration

This framework for Person Alert Codes is the **first draft**, developed to help housing providers better identify and respond to tenant needs. The design has been inspired by practices from various organisations in housing, health, and social care sectors, combining their approaches to risk, support, and safety, such as NHS, SNOMED, DWP, SAVII and HACT.  

We welcome **feedback, suggestions, and collaboration** from all users—whether you are from housing, data, or frontline services. Your input will help refine these codes and ensure they are practical, relevant, and effective for the people they are designed to protect and support.

