# Survey Data Analytics

Survey-style data modeling and reporting focused on a wide-table analytical dataset.

## Project Overview
This project contains a Power BI report and semantic model built around a survey dataset with a large number of columns and multiple response dimensions. The work focuses on structured exploration and analytical reporting rather than a production operational system.

## Business Context
This is a self-initiated learning and analytical project based on a local survey dataset. The business problem is exploratory: understand patterns across respondents, categories, criteria, and performance dimensions without requiring a live production source.

## Problem
The project needed a clear way to model a wide survey dataset in Power BI and expose the relationships between audit, score, task, and category data in a reporting layer.

## Solution
The solution includes a PBIP project, a Power BI report, and a TMDL semantic model that connect the underlying survey structure to report visuals and measures. The model organizes the dataset into fact and dimension tables for analysis.

## Data
- Source type: Microsoft Excel workbook
- Data nature: local survey dataset
- Key files: Survey.xlsx, Survay.pbip, Survay.Report, Survay.SemanticModel
- Evidence: report and semantic model are present in the project files

## Technical Approach
- Import the workbook into Power BI
- Model survey, audit, and scoring tables in a semantic layer
- Define relationships and measure logic in the model
- Present findings through a report page built in PBIR format

## Key Analytical Areas
- survey response analysis
- category and criterion profiling
- task and audit trends
- report-layer exploration across wide-table data

## Evidence / Scope
This repository contains the core project artifacts, including the PBIP, PBIX, report definition, TMDL semantic model, and the source workbook. It is best understood as a local learning project rather than a production deployment.

## Limitations
- synthetic or educational scope rather than live operational reporting
- no production deployment evidence
- no external data source integration evidence

## Repository Structure
- Survay.pbip — Power BI project file
- Survay.Report — report definition files
- Survay.SemanticModel — semantic model definitions
- Survey.xlsx — local source workbook
- PROJECT_AUDIT.md — project evidence summary

## Tools & Technologies
- Power BI
- Excel
- PBIP/PBIR/TMDL model structure

## Project Status
Self-initiated learning project with verified local evidence. No production or client deployment claims are made.
