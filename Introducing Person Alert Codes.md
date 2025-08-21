# Introducing to Person Alert Codes

## Table of contents
- [Introduction](#introduction)
- [Objectives](#objectives)
- [What's included in the data model](#whats-included-in-the-data-model)
- [How the data model can help you in future](#how-the-data-model-can-help-you-in-the-future)

## Introduction

The Person Alert Codes Module is designed to provide a structured, standardised, and interoperable way of recording alerts about individuals within the housing sector. It aims to enhance how social landlords record, manage, and share critical information about tenant and household circumstances that may require adjustments, safeguarding, or specialist responses. The system aims to improve tenant safety, ensure legal compliance, and enable data interoperability across housing management systems.
This document serves as a sector-wide guidance and implementation framework aligned with the HACT UK Housing Data Standards and MHCLG priorities, including Awaab's Law, safeguarding responsibilities, and equality, diversity, and inclusion (EDI) obligations.

The codes list was developed drawing inspiration from established frameworks to ensure consistency and sector relevance. NHS and SNOMED informed medical terminology, DWP influenced welfare-related alerts, SAVII guided social care and safeguarding practices, and HACT provided housing data standards. Combining these sources ensures the codes are comprehensive, practical, and interoperable, supporting accurate recording, risk identification, and coordinated service delivery.

### The issue

In the housing sector, information about tenants’ specific needs, risks, or vulnerabilities is often stored inconsistently across organisations. This leads to difficulties in sharing, auditing, and responding to alerts. Problems include fragmented data, inconsistent terminology, and lack of accountability for updates.
The absence of a standardised framework can result in critical information being missed or misinterpreted, potentially leading to harm, service failures, or breaches of regulatory requirements.

### Who it affects

This issue affects housing providers, local authorities, care and support organisations, and ultimately the tenants themselves. It impacts frontline housing officers, maintenance teams, contractors, social workers, and emergency services who rely on accurate information to make informed decisions.

### What has been done

The Person Alert Codes Data Model has been developed in line with the Housing Data Standards (HACT) and aligned with regulatory requirements from MHCLG. The model is interoperable with the wider housing data ecosystem, enabling integration with tenancy, repairs, compliance, and asset management systems.

## Objectives

* Ensure accurate, consistent recording of personal circumstances impacting service delivery.
* Support data interoperability across systems and organisations.
* Enable risk identification and support planning for vulnerable residents.
* Facilitate role-based access control to protect sensitive data.
* Comply with statutory duties, such as those arising from Awaab's Law, the Equality Act 2010, and safeguarding regulations.

## What's included in the data model

The model includes core tables for managing alerts, their categories, codes, and history, with foreign keys to related tables such as person, organisation, and source types. It supports auditability with created/updated by fields, progress tracking, and effective dating.

### Tables and their purpose

1. **person_alert** - Stores active alerts about a specific person so staff can quickly see important issues affecting their safety, wellbeing, or housing needs.
2. **person_alert_codes** - Holds the master list of possible alert types with clear names and descriptions for consistent use across the organisation.
3. **alert_categories** - Groups alert types into broader themes like Medical or Safeguarding so they’re easier to manage and report on.
4. **person_alert_history** - Keeps a record of every change made to a person’s alert to maintain transparency and meet compliance requirements.
5. **source_types** - Identifies where an alert came from (such as a GP or social worker) so the source is always clear for action and follow-up.
6. **special_category_data_types** – Defines data types considered sensitive under ICO guidance (e.g. health, ethnicity, religion), ensuring alerts involving special category data are flagged and handled with appropriate safeguards.  


### Integration with other modules

Alerts integrate with other housing modules, influencing repairs priorities and contractor instructions, guiding tenancy support and risk assessments, and surfacing in CRM systems to flag special requirements during contact. This ensures that vital information is shared across teams for coordinated and responsive service delivery.

## How the data model can help you in the future

This model equips housing associations with a standardised, scalable framework for capturing and managing person-specific alerts, ensuring critical health, safety, and support information is consistently recorded and easily accessible across systems. By integrating seamlessly with existing housing, repairs, and CRM modules, it enables more informed decision-making, proactive risk management, and targeted service delivery. Over time, the structured and well-governed data will support advanced analytics, AI-driven insights, and automation, helping organisations predict needs, prioritise resources, and improve tenant outcomes while meeting regulatory and safeguarding obligations.
