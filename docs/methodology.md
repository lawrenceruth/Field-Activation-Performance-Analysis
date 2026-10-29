# Methodology & Technical Notes

## 1. Business questions
- **Activity:** Which outlets and task types drive activity? How is it spread across areas?
- **Promoter performance:** Who has higher or lower average completion time? How does it vary by area?
- **Work completion:** What share of logged activity is completed, overdue, pending?
- **Quality:** What is the average score, and how does it change by area?
- **Management:** Which areas or outlets need attention, and what would improve execution?

## 2. Data preparation
Raw dataset: **1,506 rows x 9 columns** (Date, Promoter Name, Area, Outlet Name, Task Type, Tasks Completed, Completion Time (mins), Quality Score (%), Status).

| Step | What was done |
|---|---|
| Structured Table | Converted range to an Excel Table: auto-expands with new rows, structured references, easier PivotTable management, fewer excluded records |
| Blank rows | Checked, since they break PivotTables, filters, totals and charts |
| Duplicates | Temporary COUNTIFS helper column across all 9 fields; deleted afterwards to keep the original 9 columns |
| Data types | Date confirmed as a true Excel date; Tasks Completed, Completion Time (mins) and Quality Score (%) confirmed numeric |
| Completion Time | Values are **minutes**, not time-of-day (16 = 16 mins, not 0:16:00), so averages need no conversion |
| Text fields | Checked capitalisation, leading/trailing spaces, spelling, and variants in outlet, promoter, task type and status names |

## 3. Analytical framework
- **Activity concentration:** where and what type of work is performed
- **Promoter efficiency:** how long activities take
- **Work completion health:** completed vs overdue vs pending

## 4. KPI logic (cleaned_Dataset, columns M:N)
| KPI | Formula / logic | Result |
|---|---|---|
| Total Task Completed | `=SUMIF(I:I,"Completed",F:F)` | 4,715 |
| Average Completion Time | AVERAGE of Completion Time (mins) | 26.37 mins |
| Average Quality Score | AVERAGE of Quality Score (%) | 77% |

**Reconciliation:** 6,498 total task units (all statuses) vs 4,715 task units on Completed records vs 1,130 Completed records of 1,506.

## 5. PivotTables & charts
| # | Question | Rows / Columns | Values | Chart |
|---|---|---|---|---|
| 1 | Which outlets generate most activity, and what type? | Outlet Name / Task Type | Sum of Tasks Completed | Clustered column |
| 2 | Which promoters take longest? | Promoter Name | Average of Completion Time | Horizontal bar (long names read better) |
| 3 | Share of Completed / Overdue / Pending? | Status | Count of Task Type | Doughnut |

**Slicer:** Area, connected to all PivotTables/PivotCharts.

### Task-type totals (all outlets)
| Compliance Check | Outlet Visit | Product Demo | Sales Conversion | Samples Distributed | Total |
|---|---|---|---|---|---|
| 209 | 434 | 353 | 821 | 4,681 | 6,498 |

### Status counts
Completed 1,130 (75.0%) | Overdue 219 (14.5%) | Pending 157 (10.4%) | Total 1,506

## 6. Interpretation notes
- Higher completion time is a prompt to investigate, not proof of poor performance (task type, outlet environment, customer traffic, workload and complexity all affect it).
- Area slicer results show why area-level views matter beyond campaign totals.
