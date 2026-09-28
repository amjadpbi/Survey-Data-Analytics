# 60+ Columns Survey Report - Project Audit

Read-only forensic reconstruction of `D:\Power BI\60+ Columns Survey Data`. This is a learning/practice project audit, not a client, production, or enterprise assessment. No existing project, source, report, model, or documentation file was modified. Power BI Desktop was not opened, no refresh or external connection was performed, and the PBIX binary was not extracted.

## 1. Executive Summary

### Finding
The project contains a thick PBIP named `Survay`, a PBIR report, a TMDL semantic model, a local Excel workbook named `Survey.xlsx`, and a PBIX binary.

### Evidence
- `Survay.pbip`
- `Survay.Report/definition.pbir`
- `Survay.SemanticModel/definition/`
- `Survey.xlsx`
- `Survay.pbix`

### Classification
OBSERVED FACT

### Finding
The source workbook is one wide worksheet named `Sheet1`. Read-only workbook inspection reports 62 columns and 5 worksheet rows, including the header row, with 62 non-empty headers. This indicates 4 data rows in the current workbook dimensions, subject to normal Excel used-range limitations.

### Evidence
- `Survey.xlsx`, worksheet `Sheet1`.
- Read-only workbook metadata inspection.

### Classification
OBSERVED FACT

### Finding
The active model converts the wide survey structure into multiple analysis-oriented tables. `Fact_Scores` unpivots survey criteria columns into criterion/value rows, and `Fact_Tasks` unpivots task columns and splits the attribute text into task status/type. Other queries retain audit-level, date, and location structures.

### Evidence
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl`
- `Survay.SemanticModel/definition/tables/Fact_Tasks.tmdl`
- `Survay.SemanticModel/definition/tables/Fact_Audit.tmdl`
- `Survay.SemanticModel/definition/tables/Dim_Date.tmdl`
- `Survay.SemanticModel/definition/tables/Dim_Location.tmdl`

### Classification
OBSERVED FACT

### Finding
The report is a single-page executive-style survey dashboard with 12 visuals covering audit counts, locations/clients, compliance, critical issues, monthly compliance, category scoring, task status, client distribution, criteria detail, and an 85% target gauge.

### Evidence
- `Survay.Report/definition/pages/pages.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/page.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/*/visual.json`

### Classification
OBSERVED FACT

### Finding
The project demonstrates a practical learning exercise in handling a wide survey sheet with Power Query, reshaping repeated question groups into analysis tables, building a basic related semantic model, writing DAX measures, and creating a simple Power BI report. It does not provide evidence of production deployment, enterprise architecture, or advanced analytics.

### Evidence
- Creator-provided learning context.
- Active M transformations, TMDL model, deployed measures, and PBIR report.

### Classification
CREATOR-PROVIDED HISTORY plus OBSERVED FACT; production/enterprise status is UNKNOWN and not claimed.

## 2. Project Classification

### Finding
This is a learning/practice project created while learning Power BI, based on the creator-provided context. The filesystem supports a small survey-analysis solution rather than a demonstrated production business system.

### Evidence
- Creator-provided history supplied for this audit.
- `Survay.pbip`, `Survey.xlsx`, semantic-model TMDL, and one-page PBIR report.

### Classification
CREATOR-PROVIDED HISTORY plus INFERENCE.

### Implementation status
IMPLEMENTED: PBIP/PBIR/TMDL project, wide-sheet ingestion definitions, normalized fact-like queries, semantic model, measures, and report metadata.

PLANNED / DESIGNED: UNKNOWN. No separate planning document was found that establishes additional unimplemented scope.

UNKNOWN: runtime refresh, rendered report behavior, and synchronization between PBIX and PBIP.

## 3. Creator-Provided History

### Finding
The creator describes the original exercise as starting with a survey dataset containing 60+ columns in one sheet, learning how to handle a very wide source, using Power Query to make it more usable for analysis, and building a relatively simple Power BI report.

### Evidence
- Creator-provided context supplied for this audit.

### Classification
CREATOR-PROVIDED HISTORY.

### Finding
The creator states that the project was created while learning Power BI, not as a client engagement or production business solution.

### Evidence
- Creator-provided context supplied for this audit.

### Classification
CREATOR-PROVIDED HISTORY.

### Finding
The filesystem independently supports the central learning sequence: one wide workbook, embedded Excel source queries, unpivoted score/task structures, multiple semantic-model tables, DAX measures, and one report page.

### Evidence
- `Survey.xlsx`
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl`
- `Survay.SemanticModel/definition/tables/Fact_Tasks.tmdl`
- `Survay.SemanticModel/definition/tables/_Measures.tmdl`
- `Survay.Report/definition/pages/`

### Classification
OBSERVED FACT plus INFERENCE.

## 4. Project Structure

### Finding
The project boundary is the folder `60+ Columns Survey Data`, containing:

- `Survay.pbip` - PBIP project entry point.
- `Survay.Report/` - PBIR report definition and static resources.
- `Survay.SemanticModel/` - TMDL semantic model, relationships, runtime/cache files, and DAX query-view metadata.
- `Survey.xlsx` - local source workbook.
- `Survay.pbix` - binary Power BI artifact.
- `.gitignore` - project support file.

### Evidence
- Root directory inventory.
- `Survay.pbip`.
- `Survay.Report/`.
- `Survay.SemanticModel/`.
- `Survey.xlsx`.
- `Survay.pbix`.

### Classification
OBSERVED FACT.

### Finding
`Survay.pbip` points to `Survay.Report`, and `Survay.Report/definition.pbir` uses a local `byPath` model reference to `../Survay.SemanticModel`. This is a thick local PBIP report/model arrangement.

### Evidence
- `Survay.pbip`
- `Survay.Report/definition.pbir`

### Classification
OBSERVED FACT.

### Finding
The semantic-model definition contains 25 TMDL files in the project tree, including model/database/relationship/culture files, table files, generated date infrastructure, measures, legacy tables, and local date tables. No standalone `expressions.tmdl` file exists; M expressions are embedded in table partitions.

### Evidence
- `Survay.SemanticModel/definition/`
- Recursive TMDL inventory.

### Classification
OBSERVED FACT.

## 5. Source Dataset

### Finding
`Survey.xlsx` contains one worksheet: `Sheet1`. The used worksheet dimensions are 62 columns by 5 rows, with 62 non-empty headers.

### Evidence
- `Survey.xlsx`.
- Read-only `openpyxl` workbook inspection.

### Classification
OBSERVED FACT.

### Finding
The source headers include audit metadata such as `Id`, `Start time`, `Completion time`, `Email`, `Name`, `Date of Audit`, `Business Unit`, `Client`, and `Building/Location`; task-count fields; PPM review fields; fire-drill dates; observed PPM fields; log-book/testing fields; document-control/procedure fields; housekeeping fields; grooming fields; comments; month/year-month; and region.

### Evidence
- `Survey.xlsx`, `Sheet1` header row.
- Full header list obtained through read-only workbook inspection.

### Classification
OBSERVED FACT.

### Finding
The source is genuinely wide and contains repeated question-group structures encoded in long column names separated by delimiters such as periods. The current file is not a multi-sheet relational source; it is one wide survey sheet.

### Evidence
- `Survey.xlsx`, `Sheet1` headers such as `Review Five Completed PPM's from Previous Month...`, `Observe two PPM Tasks Being Carried Out...`, `Log Books & Testing...`, `Document Control & Procedures...`, `House Keeping Standards...`, and `Grooming Standards...`.

### Classification
OBSERVED FACT.

### Finding
The current workbook's physical row count is small: 5 worksheet rows including the header. Whether Excel's used range accurately represents all historical intended survey responses is UNKNOWN.

### Evidence
- `Survey.xlsx`, read-only workbook dimensions.

### Classification
OBSERVED FACT for the workbook dimensions; UNKNOWN for historical completeness.

### Finding
The current local workbook is not the path referenced by the active TMDL partitions. Several active-looking partitions reference `D:\Power BI\Survey.xlsx`, while legacy tables reference `C:\Users\hp\Downloads\Survey_Dummy_Data.xlsx`. The included workbook is `60+ Columns Survey Data\Survey.xlsx`.

### Evidence
- `Survey.xlsx`
- `Survay.SemanticModel/definition/tables/Fact_Audit.tmdl`
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl`
- `Survay.SemanticModel/definition/tables/Fact_Tasks.tmdl`
- `Survay.SemanticModel/definition/tables/Audit.tmdl`
- `Survay.SemanticModel/definition/tables/Sheet1.tmdl`

### Classification
OBSERVED FACT; refresh portability is a POTENTIAL GAP.

## 6. Power Query Transformation

### Finding
The active audit-level path is:

```text
Excel.Workbook(File.Contents("D:\Power BI\Survey.xlsx"))
  -> Sheet1 navigation
  -> Table.PromoteHeaders
  -> rename/remove/type/date/client transformations
  -> Fact_Audit
```

`Fact_Audit` renames `Id` to `Audit_ID` and `Name` to `Auditor_Name`, removes `Email`, converts and remaps selected date values to date keys, maps client names to numeric location keys, removes unused location/business-unit columns, appends legacy `Audit`, and loads the resulting audit-level table.

### Evidence
- `Survay.SemanticModel/definition/tables/Fact_Audit.tmdl`

### Classification
OBSERVED FACT.

### Finding
The score-normalization path is:

```text
Excel.Workbook(File.Contents("D:\Power BI\Survey.xlsx"))
  -> Sheet1 navigation
  -> promote headers
  -> duplicate Id as Audit_Id
  -> remove audit-level metadata
  -> Table.UnpivotOtherColumns
  -> trim Attribute/Value
  -> replace Yes with 5 and No with 0
  -> integer conversion with error replacement to null
  -> rename Attribute to Criteria_Name
  -> append legacy Sheet1
  -> Fact_Scores
```

This is the main wide-to-long normalization step for scored survey fields.

### Evidence
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl`
- M operations `Table.UnpivotOtherColumns`, `Table.ReplaceValue`, `Table.ReplaceErrorValues`, and `Table.Combine`.

### Classification
OBSERVED FACT / IMPLEMENTED.

### Finding
The task-normalization path is:

```text
Excel.Workbook(File.Contents("D:\Power BI\Survey.xlsx"))
  -> Sheet1 navigation
  -> remove audit metadata and scored survey fields
  -> Table.UnpivotOtherColumns
  -> split Attribute text multiple times
  -> derive Task_Status and Task_Type
  -> convert Value to Task_Count
  -> append legacy Sheet1 (6)
  -> Fact_Tasks
```

### Evidence
- `Survay.SemanticModel/definition/tables/Fact_Tasks.tmdl`
- M operations `Table.UnpivotOtherColumns`, `Table.SplitColumn`, `Table.Combine`, and type conversion.

### Classification
OBSERVED FACT / IMPLEMENTED.

### Finding
The dimension paths include:

- `Dim_Location`: retain location-related fields, rename/type fields, append legacy `Location`.
- `Dim_Date`: remove unrelated fields, split `YEAR-MONTH`, derive year, deduplicate by audit date, append legacy `Date`, and derive a month sort field.
- `Dim_Category`, `Dim_Criteria`, and `Hierarchy`: static/calculated supporting structures rather than direct wide-sheet unpivot outputs.

### Evidence
- `Survay.SemanticModel/definition/tables/Dim_Location.tmdl`
- `Survay.SemanticModel/definition/tables/Dim_Date.tmdl`
- `Survay.SemanticModel/definition/tables/Dim_Category.tmdl`
- `Survay.SemanticModel/definition/tables/Dim_Criteria.tmdl`
- `Survay.SemanticModel/definition/tables/Hierarchy.tmdl`

### Classification
OBSERVED FACT.

### Finding
No evidence of Power Query pivoting, merge/nested-join operations, or custom M functions was found in the inspected partitions. The core transformations are workbook navigation, header promotion, column selection/removal/renaming, type/date conversions, unpivoting, splitting, appending, and calculated columns.

### Evidence
- Recursive operation scan across `Survay.SemanticModel/definition/tables/*.tmdl`.
- Active/legacy table partitions.

### Classification
OBSERVED FACT.

### Finding
The model includes both current-looking normalized queries and legacy duplicate queries. The active normalized queries append legacy tables such as `Audit`, `Sheet1`, `Sheet1 (6)`, `Location`, and `Date`; the exact reason for this duplication is not documented.

### Evidence
- `Fact_Audit.tmdl`
- `Fact_Scores.tmdl`
- `Fact_Tasks.tmdl`
- `Dim_Location.tmdl`
- `Dim_Date.tmdl`
- Legacy table TMDLs under `Survay.SemanticModel/definition/tables/`

### Classification
OBSERVED FACT; historical intent is UNKNOWN.

## 7. Before -> After Data Structure

### Finding
The source-to-model shape is:

```text
Before:
  one Sheet1 worksheet
  62 columns
  audit metadata + task counts + dates + long-form survey question columns

After:
  Fact_Audit      audit-level records and audit metadata
  Fact_Scores     one audit/criterion/value-style structure after unpivoting
  Fact_Tasks      one audit/task-status/task-type/count-style structure after unpivoting
  Dim_Date        date attributes and month sorting
  Dim_Location    client/location attributes
  Dim_Category    survey category metadata and weights
  Dim_Criteria    criterion metadata and maximum points
  Hierarchy       criteria/category presentation structure
```

### Evidence
- `Survey.xlsx`
- `Fact_Audit.tmdl`
- `Fact_Scores.tmdl`
- `Fact_Tasks.tmdl`
- `Dim_Date.tmdl`
- `Dim_Location.tmdl`
- `Dim_Category.tmdl`
- `Dim_Criteria.tmdl`
- `Hierarchy.tmdl`

### Classification
OBSERVED FACT plus INFERENCE about table roles.

### Finding
The dataset is normalized for reporting in the practical sense that repeated survey question columns are converted to attribute/value-style rows for scores and tasks. This is not evidence of a fully normalized enterprise data model.

### Evidence
- `Fact_Scores.tmdl`: `Table.UnpivotOtherColumns` and `Criteria_Name`/`Value` output.
- `Fact_Tasks.tmdl`: `Table.UnpivotOtherColumns` and `Task_Type`/`Task_Status`/`Task_Count` output.
- Relationship and table definitions.

### Classification
INFERENCE grounded in observed transformations.

### Finding
Exact resulting row counts cannot be established from the model files alone because the active partitions reference external absolute paths and no refresh was executed. The TMDL establishes resulting schemas and transformations, not current loaded row counts.

### Evidence
- Active source paths in table partitions.
- No Power BI refresh or external file substitution was performed.

### Classification
UNKNOWN.

## 8. Semantic Model

### Finding
The model contains current/normalized tables:

- Facts: `Fact_Audit`, `Fact_Scores`, `Fact_Tasks`.
- Dimensions/supporting tables: `Dim_Date`, `Dim_Location`, `Dim_Category`, `Dim_Criteria`, `Hierarchy`.
- Measure table: `_Measures`.
- Legacy/hidden or supporting tables: `Audit`, `Date`, `Location`, `Sheet1`, `Sheet1 (6)`.
- Generated date infrastructure: one date template and six local date tables.

### Evidence
- `Survay.SemanticModel/definition/model.tmdl`
- `Survay.SemanticModel/definition/tables/`

### Classification
OBSERVED FACT.

### Finding
The active model is multiple-table and star-like rather than a single table. The evidence supports an audit fact, score fact, task fact, shared date/location structures, criteria/category metadata, and a criteria hierarchy. The model is more accurately described as a small survey star-style model with legacy duplicate/supporting tables than as a pure normalized warehouse.

### Evidence
- `Survay.SemanticModel/definition/relationships.tmdl`
- Table TMDLs.

### Classification
INFERENCE.

### Finding
The model contains 13 relationship definitions. They include fact-to-dimension links, fact-to-fact audit links, criteria/category/hierarchy links, and automatic local date-table relationships. Exact cardinality and filter direction are not consistently serialized in the inspected TMDL.

### Evidence
- `Survay.SemanticModel/definition/relationships.tmdl`

### Classification
OBSERVED FACT; exact cardinality/filter behavior UNKNOWN where not explicit.

### Finding
`Fact_Scores[Criteria_Key]` is an authored calculated column using DAX `LOOKUPVALUE` and `CONTAINSSTRING` against `Dim_Criteria`. `Hierarchy` contains an authored calculated column. No other authored calculated tables were established beyond static/calculated support tables visible in the TMDL.

### Evidence
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl`
- `Survay.SemanticModel/definition/tables/Hierarchy.tmdl`
- TMDL table inventory.

### Classification
OBSERVED FACT.

### Finding
The model contains 32 deployed measures in `_Measures.tmdl`. Measures cover audit counts, task status/completion, scoring/compliance, category-specific scores, target comparison, client ranking, category ranking, location comparison, status indicators, and dashboard title text.

### Evidence
- `Survay.SemanticModel/definition/tables/_Measures.tmdl`

### Classification
OBSERVED FACT.

### Finding
The report’s active semantic-model binding is local `byPath`, but current table partitions reference absolute external paths instead of the included workbook path. Whether the PBIP was authored on another machine/path or is currently refreshable is UNKNOWN.

### Evidence
- `Survay.Report/definition.pbir`
- `Fact_Audit.tmdl`, `Fact_Scores.tmdl`, `Fact_Tasks.tmdl`
- `Survey.xlsx`

### Classification
OBSERVED FACT; refreshability UNKNOWN.

## 9. DAX / Calculations

### Finding
The deployed measures include the following meaningful groups:

- Audit volume: `Total Audits`.
- Tasks: `Total Open Tasks`, `Total Closed Tasks`, `Task Completion Rate`, `Reactive Task Completion %`, `PPM Task Completion %`, `Task Backlog`.
- Scores: `Total Score Achieved (Category)`, `Total Possible Score`, `Compliance Score %`, `Weighted Compliance Score`, `Category Compliance %`, `Max Score`.
- Issue/quality indicators: `Critical Issues Count`, `Status Color`, `Status Indicator`.
- Category-specific scores: `PPM Quality Score %`, `Grooming Standards Score %`, `Field Observation Score %`, `Housekeeping Score %`.
- Ranking/comparison: `Client Rank`, `Best Performing Category`, `Worst Performing Category`, `Location Performance vs Avg`.
- Context/title: `Selected Client`, `Audits for Selected Location`, `Dashboard Title`.
- Additional measures: `Criteria Pass Rate`, `Avg Score Per Audit`, `Target Compliance`, `Compliance vs Target`, and an undeclared-expression `Task Status %` measure.

### Evidence
- `Survay.SemanticModel/definition/tables/_Measures.tmdl`

### Classification
OBSERVED FACT.

### Finding
The main score logic calculates achieved values and possible values from `Fact_Scores` and `Dim_Criteria[Max_Points]`; compliance is expressed as a ratio. Task measures aggregate `Fact_Tasks[Task_Count]` by open/closed status and task type. Client/category/location measures operate through the model relationships and DAX filters.

### Evidence
- `_Measures.tmdl`
- `relationships.tmdl`
- `Dim_Criteria.tmdl`
- `Fact_Scores.tmdl`
- `Fact_Tasks.tmdl`

### Classification
OBSERVED FACT.

### Finding
Static potential concerns include the undeclared-expression `Task Status %` measure and the fact that score criteria are mapped using substring matching (`CONTAINSSTRING`) in a calculated column. These are static observations only; no runtime failure or incorrect result is claimed.

### Evidence
- `_Measures.tmdl`, `Task Status %`.
- `Fact_Scores.tmdl`, `Criteria_Key` calculated column.

### Classification
POTENTIAL ISSUE / UNKNOWN runtime impact.

### Finding
No DAX measures were executed, so numerical correctness, filter-context behavior, and performance are UNKNOWN.

### Evidence
- `_Measures.tmdl`
- No Power BI Desktop, Tabular Editor, or external model query execution.

### Classification
UNKNOWN.

## 10. Report Structure

### Finding
The PBIR report contains one visible page named `Executive Dashboard`, with a 1280 x 1200 canvas and 12 visual JSON files.

### Evidence
- `Survay.Report/definition/pages/pages.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/page.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/`

### Classification
OBSERVED FACT.

### Finding
The visual inventory is:

- 5 cards: audit count, location count, compliance score, critical issues, and dashboard title.
- 1 dropdown slicer for `Dim_Location[Client]`.
- 1 line chart for monthly compliance score.
- 1 clustered bar chart for achieved versus possible score by category.
- 1 line/clustered-column combo chart for open and closed tasks by type.
- 1 donut chart for audit count by client.
- 1 pivot table/matrix for category/criteria scores and compliance.
- 1 gauge for compliance score against an 85% target.

### Evidence
- Individual visual JSON files under `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/`.
- `Survay.Report/definition/report.json`.

### Classification
OBSERVED FACT.

### Finding
The report contains a shared base theme `CY25SU11`. No bookmarks, report extensions, custom visuals, or additional pages were found in the inspected PBIR tree.

### Evidence
- `Survay.Report/definition/report.json`
- `Survay.Report/StaticResources/SharedResources/BaseThemes/CY25SU11.json`
- PBIR file inventory.

### Classification
OBSERVED FACT.

### Finding
Visual-level filters exclude blank and `Operational Performance` category values in the matrix and category bar chart. Visual containers generally specify `drillFilterOtherVisuals: true`. No report-level or page-level filter configuration was observed.

### Evidence
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/4ad340721be462950b3d/visual.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/d33117ccd9debd12cd69/visual.json`
- `Survay.Report/definition/report.json`
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/page.json`

### Classification
OBSERVED FACT.

### Finding
The report can answer questions about audit volume, client/location coverage, overall and category compliance, monthly compliance trend, criteria-level achieved versus required scores, zero-score/critical issues, open versus closed task counts by type, client distribution, and performance against the 85% target. These are metadata-supported analytical questions, not observed rendered outputs.

### Evidence
- `_Measures.tmdl`
- PBIR visual bindings.

### Classification
INFERENCE grounded in report/model metadata.

## 11. End-to-End Lineage

### Finding
The file-defined lineage is:

```text
Survey.xlsx Sheet1
  -> Excel.Workbook + Sheet1 navigation
  -> Table.PromoteHeaders
  -> Fact_Audit / Fact_Scores / Fact_Tasks / Dim_Date / Dim_Location transformations
  -> unpivoted score and task structures
  -> TMDL semantic model relationships
  -> 32 DAX measures
  -> one-page PBIR Executive Dashboard
```

### Evidence
- `Survey.xlsx`
- Active/current table partitions under `Survay.SemanticModel/definition/tables/`
- `relationships.tmdl`
- `_Measures.tmdl`
- PBIR page and visual files.

### Classification
OBSERVED FACT for the defined pipeline; runtime execution UNKNOWN.

### Finding
The project also contains a legacy duplicate lineage using `C:\Users\hp\Downloads\Survey_Dummy_Data.xlsx` and legacy tables such as `Audit`, `Date`, `Location`, `Sheet1`, and `Sheet1 (6)`. The exact historical relationship between current and legacy query sets is not documented.

### Evidence
- Legacy table TMDLs.
- Active queries that append legacy tables.
- `model.tmdl` table references.

### Classification
OBSERVED FACT; historical intent UNKNOWN.

## 12. Learning Objectives Demonstrated

### Finding
The project demonstrates the following learning skills:

- Inspecting and handling a genuinely wide Excel survey sheet.
- Promoting headers and selecting/removing/renaming columns.
- Converting a wide score/question structure to long rows with `Table.UnpivotOtherColumns`.
- Converting task question columns into task type/status/count fields through unpivoting and text splitting.
- Building separate audit, score, task, date, location, category, and criteria structures.
- Creating relationships between facts and supporting dimensions.
- Writing basic DAX measures for compliance, task counts, rankings, targets, and dashboard text.
- Building a simple one-page Power BI dashboard with slicers, cards, charts, matrix, and gauge.

### Evidence
- `Survey.xlsx`
- `Fact_Scores.tmdl`
- `Fact_Tasks.tmdl`
- `Survay.SemanticModel/definition/relationships.tmdl`
- `_Measures.tmdl`
- PBIR visual files.

### Classification
OBSERVED FACT plus CREATOR-PROVIDED HISTORY.

### Finding
The central learning demonstration is wide-to-long survey transformation for analysis. The project does not demonstrate a production ingestion service, enterprise data warehouse, advanced analytics, or verified operational deployment.

### Evidence
- Creator-provided learning context.
- Active local workbook/PBIP/TMDL/PBIR structure.
- No external service, deployment, or runtime evidence in this audit.

### Classification
INFERENCE / UNKNOWN for any external deployment.

## 13. Implemented vs Planned

### Implemented

- Thick PBIP/PBIR/TMDL project structure.
- Excel workbook navigation through embedded M partitions.
- Wide-sheet cleanup, type conversion, column removal/renaming, unpivoting, task-field splitting, appending, and static dimension construction.
- Multiple semantic-model tables and 13 relationship definitions.
- 32 deployed measures.
- One-page report with 12 visuals, client slicer, filters, theme, and gauge target.

### Evidence
- Project root inventory.
- Active table TMDLs.
- `relationships.tmdl`.
- `_Measures.tmdl`.
- PBIR files.

### Classification
IMPLEMENTED.

### Planned / Designed

No separate planned feature set was established from the project files. Any additional learning intentions beyond the creator-provided wide-survey exercise are UNKNOWN.

### Evidence
- No project planning document was found in the inventory.
- Creator-provided context describes the learning objective but does not specify additional planned features.

### Classification
UNKNOWN.

### Partially Implemented / Historical Boundary

- Current normalized queries coexist with legacy duplicate tables and appended legacy query outputs.
- The included `Survey.xlsx` exists locally, but current partitions reference absolute paths outside the project.
- The semantic model contains a measure named `Task Status %` without an expression; it is not established as active report functionality.
- The PBIX exists, but PBIX/PBIP synchronization is unknown.

### Evidence
- Active and legacy TMDLs.
- Absolute source paths.
- `_Measures.tmdl`.
- `Survay.pbix` and `Survay.pbip`.

### Classification
OBSERVED FACT / UNKNOWN runtime and historical status.

## 14. Portfolio Relevance

### Finding
As a supporting learning project, this project demonstrates the ability to take a wide survey sheet and reshape it into more usable score/task structures with Power Query, then build a simple related Power BI report.

### Evidence
- `Survey.xlsx`
- `Fact_Scores.tmdl`
- `Fact_Tasks.tmdl`
- `_Measures.tmdl`
- PBIR visual files.

### Classification
INFERENCE grounded in observed implementation and creator-provided history.

### Finding
The project is worth keeping as evidence of learning Power Query normalization, basic model construction, and basic report creation. This is a factual characterization, not a portfolio ranking or marketing recommendation.

### Evidence
- Creator-provided context.
- Active transformation/model/report artifacts.

### Classification
CREATOR-PROVIDED HISTORY plus INFERENCE.

### Finding
The project does not demonstrate, based on available evidence, production deployment, enterprise architecture, advanced analytics, external-service lineage, or validated refresh/runtime behavior.

### Evidence
- Project inventory.
- No external connection, refresh, deployment, or runtime validation performed.

### Classification
UNKNOWN / NOT DEMONSTRATED BY AVAILABLE ARTIFACTS.

## 15. Limitations / Unknowns

### Finding
The following were not established:

- Actual refresh success using any referenced absolute source path.
- Whether the included `Survey.xlsx` is the exact workbook used to produce the current PBIP state.
- Actual loaded row counts after Power Query execution.
- Numerical DAX correctness or performance.
- Rendered report appearance and visual interaction behavior.
- PBIX/PBIP synchronization.
- Exact historical reason for legacy duplicate tables and append operations.
- Whether `C:\Users\hp\Downloads\Survey_Dummy_Data.xlsx` exists or remains relevant.
- Whether the absolute `D:\Power BI\Survey.xlsx` path is available on the authoring machine.
- Complete historical survey response volume beyond the current workbook used range.

### Evidence
- Absolute paths in table partitions.
- `Survey.xlsx` local workbook.
- PBIX binary.
- No refresh/runtime/external execution performed.

### Classification
UNKNOWN.

### Finding
The PBIX was treated as an opaque binary and was not unzipped, extracted, or reverse-engineered. The audit relies on PBIP/PBIR/TMDL and readable workbook metadata.

### Evidence
- `Survay.pbix`
- PBIP/PBIR/TMDL file inventory.

### Classification
OBSERVED LIMITATION.

### Finding
The current workbook was inspected for sheet dimensions and headers, but no exhaustive row-level profiling was performed because the learning objective is structural reconstruction rather than data-quality profiling.

### Evidence
- `Survey.xlsx` read-only workbook inspection.

### Classification
OBSERVED LIMITATION.

## 16. Evidence Summary

### Project files

- `Survay.pbip` - PBIP entry point.
- `Survay.Report/definition.pbir` - local semantic-model binding.
- `Survay.Report/definition/pages/pages.json` - page order and active page.
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/page.json` - Executive Dashboard metadata.
- `Survay.Report/definition/pages/5f358f1263069ed4fff3/visuals/*/visual.json` - visual types, bindings, filters, and interaction metadata.
- `Survay.Report/definition/report.json` - report settings and theme reference.
- `Survay.Report/StaticResources/SharedResources/BaseThemes/CY25SU11.json` - base theme resource.
- `Survay.SemanticModel/definition/model.tmdl` - model table references and model metadata.
- `Survay.SemanticModel/definition/relationships.tmdl` - 13 relationship definitions.
- `Survay.SemanticModel/definition/tables/Fact_Audit.tmdl` - audit-level Power Query output.
- `Survay.SemanticModel/definition/tables/Fact_Scores.tmdl` - score unpivot/normalization.
- `Survay.SemanticModel/definition/tables/Fact_Tasks.tmdl` - task unpivot/splitting.
- `Survay.SemanticModel/definition/tables/Dim_Date.tmdl` - date transformation.
- `Survay.SemanticModel/definition/tables/Dim_Location.tmdl` - location transformation.
- `Survay.SemanticModel/definition/tables/Dim_Category.tmdl` - category structure.
- `Survay.SemanticModel/definition/tables/Dim_Criteria.tmdl` - criteria/max-point structure.
- `Survay.SemanticModel/definition/tables/Hierarchy.tmdl` - category/criteria hierarchy.
- `Survay.SemanticModel/definition/tables/_Measures.tmdl` - 32 deployed measures.

### Source file

- `Survey.xlsx` - one `Sheet1` worksheet, 62 columns, 5 worksheet rows reported by read-only workbook inspection.

### Audit boundary

- Creator-provided history is explicitly separated from filesystem evidence.
- No existing project/source/report/model file was modified.
- No external service or database was contacted.
- No refresh, DAX execution, or report rendering was performed.
