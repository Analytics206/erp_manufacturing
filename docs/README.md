# Valor ERP Documentation

This directory contains comprehensive documentation for the Valor ERP Manufacturing project. Use this index to navigate through the various documentation files.

## Core Documentation

| Document Name      | Description   |
|--------------------|---------------|
| [1-project_charter.md](./1-project_charter.md) | Key project objectives, scope, stakeholders, and success criteria for the Valor ERP Manufacturing system. |
| [2-business_requirements.md](./2-business_requirements.md) | Business requirements document (BRD) outlining the business goals, stakeholder needs, success criteria. |
| [3-product_requirements.md](./3-product_requirements.md) | Product requirements document (PRD) detailing specific product features, acceptance criteria, and prioritization. |
| [4-requirements_tracker.md](./4-requirements_tracker.md) | Tracking document for requirement implementation status and progress across the ERP manufacturing modules. |
| [6-system_design.md](./6-system_design.md) | Details the system architecture, design patterns, configuration options, and component relationships that comprise the Valor ERP Manufacturing system. |
| [7-tech_stack.md](./7-tech_stack.md) | Comprehensive overview of all technologies used in the project including the cloud-native architecture, Firebase backend, and Next.js frontend. |
| [8-schema.md](./8-schema.md) | Database schema documentation for the manufacturing-specific entities including WorkCenters, Machines, Operations, ProductionOrders, Quality Inspections. |

## Project Management & Planning

| Document Name     | Description   |
|-----------------|---------------|
| [0-dev_notes.md](./0-dev_notes.md) | Developer notes and informal documentation about ongoing development work. |
| [5-scope_statement.md](./5-scope_statement.md) | Detailed scope definition for the ERP Manufacturing project, outlining boundaries and deliverables. |
| [9-project_plan.md](./9-project_plan.md) | Project timeline, milestones, resource allocation, and delivery schedule for the manufacturing ERP system. |
| [10-communication_plan.md](./10-communication_plan.md) | Guidelines for team communication, reporting structures, and stakeholder engagement throughout the project. |
| [12-risk_management_plan.md](./12-risk_management_plan.md) | Identification, assessment, and mitigation strategies for project risks and contingency plans. |

## Release & Support Documentation

| Document Name     | Description   |
|-----------------|---------------|
| [11-release_notes.md](./11-release_notes.md) | Chronological record of all releases, with version details, features, enhancements, and dependencies for each update. |
| [13-scratch.md](./13-scratch.md) | Working document for temporary notes and development ideas. |
| [EmojiMe.md](./EmojiMe.md) | Emoji-based communication guidelines for the project documentation and team collaboration. |
| [markdown_cheatsheet.md](./markdown_cheatsheet.md) | Reference guide for markdown formatting used in the project documentation. |

## Additional Resources

| Directory Name     | Description   |
|--------------------|---------------|
| [feedback](./feedback) | User feedback collection and analysis for continuous product improvement. |
| [product_eval](./product_eval) | Product evaluation metrics, testing results, and quality assessment documentation. |
| [setup](./setup) | Setup instructions, configuration guides, and deployment procedures for the ERP system. |

## About This Documentation

The documentation in this repository follows these principles:

1. **Comprehensive Coverage**: Documentation covers technical, business, and operational aspects of the manufacturing ERP
2. **Chronological Tracking**: Release notes and version tracking provide historical record of system development
3. **Clear Organization**: Documentation is categorized by purpose and target audience with consistent numbering
4. **Technical Accuracy**: System specifications and database schema are precisely documented
5. **Ongoing Maintenance**: Documentation is updated alongside code changes and schema enhancements

## Recent Major Developments

The ERP Manufacturing project schema was recently enhanced with:

- **Manufacturing-specific entities**: WorkCenters, Machines, Operations, ProductionOrders, QualityInspections, MaterialRequirements, and BillOfMaterials
- **Normalized address structure**: CustomerShippingAddresses and CustomerBillingAddresses with support for multiple addresses per customer
- **Data integrity improvements**: Soft delete flags, timestamps, audit logging, and polymorphic references
- **Enhanced schema documentation**: Visual entity relationship diagrams and detailed entity descriptions

## Guidelines for Documentation Contributors

When updating or adding documentation:

1. Follow the established formatting patterns and numbering convention
2. Update release_notes.md when adding new features
3. Keep system_design.md, tech_stack.md, and schema.md current with architectural and data model changes
4. Use descriptive filenames that indicate document purpose
5. Ensure cross-references between documents are maintained

---

*This index was last updated: June 10, 2025*
