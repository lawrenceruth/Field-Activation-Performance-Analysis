# Where Is GlowRoot's Field Effort Going, and How Much of It Gets Finished?

*Field Activation Performance Dashboard · Microsoft Excel · Retail Activation Analytics*

![Dashboard](assets/dashboard.png)

## The business problem
GlowRoot Naturals, a skincare and haircare brand, runs an in-store promoter campaign across retail outlets in Lagos. Promoters log their daily work: outlet visits, compliance checks, product demos, sales conversions and samples distributed.

The log is a flat file of 1,506 rows. It tells the Trade Marketing team everything and nothing at a glance. Management needed quick answers to three questions:

1. **Where is field activity concentrated**, by outlet, area and task type?
2. **How long do promoters take** to complete their activities?
3. **How much of the logged work is actually finished**, and how much is overdue or still pending?

This project turns that log into a single-page, interactive Excel dashboard that answers them, with an Area slicer so a manager can move from the campaign total to any one area.

## What the analysis shows

**Sampling is the campaign.** Of 6,498 task units logged, 4,681 (about 72%) are samples distributed. Sales conversions (821) and product demos (353) are far smaller, so the campaign's output is overwhelmingly sampling.

**Effort is uneven across outlets.** Justrite Yaba (671), Ebeano Supermarket (665), Grand Square Ikeja (592) and SPAR Ikorodu (536) lead. Shoprite Ikeja logged just 116.

**About three-quarters of the work is done; a real backlog remains.** 1,130 of 1,506 records (75.0%) are completed. The other 376 are outstanding: **219 overdue (14.5%)** and **157 pending (10.4%)**. Overdue is the larger group, meaning those activities have already missed their expected completion point.

**Completion time varies between promoters.** The overall average is **26.37 minutes**, while promoter averages run from **21.39 to 33.33 minutes**.

**Completion rates differ by area**, which the totals hide:

| Area | Completed | Overdue | Pending | Records | Completion rate |
|---|---|---|---|---|---|
| Yaba | 185 | 25 | 21 | 231 | ~80.1% |
| Lekki | 177 | 34 | 24 | 235 | ~75.3% |
| Onikan | 39 | 5 | 9 | 53 | ~73.6% |

Average quality score across all activities is **77%**.

## Dashboard KPIs
| KPI | Value | How it is calculated |
|---|---|---|
| Total Task Completed | 4,715 | Sum of *Tasks Completed* where Status = Completed |
| Average Completion Time | 26.37 mins | Average of *Completion Time (mins)* |
| Average Quality Score | 77% | Average of *Quality Score (%)* |

**Read the task numbers carefully.** 6,498 is task units across *all* statuses; 4,715 is task units on *completed* records only; 1,130 is the count of completed *records*. They measure different things and should not be quoted interchangeably.

## What I would recommend
- **Find out why outlet volumes differ so much.** Customer traffic, promoter allocation, outlet characteristics and campaign requirements are the first things to rule in or out.
- **Work the overdue list first**, then set a routine for reviewing it so items do not age.
- **Triage pending items:** complete, reschedule or reassign.
- **Do not judge promoters on completion time alone.** Compare against task mix, outlet and workload first.
- **Check whether sampling converts.** With 72% of effort in sampling, look at how Samples Distributed relates to Product Demos and Sales Conversions.

## Limits of this analysis
The data shows patterns, not causes. It has no customer traffic, task complexity, promoter experience or travel distance, so a longer completion time is not proof of lower productivity, and heavy sampling is not proof of campaign effectiveness. Treat the dashboard as a way to decide where to look next.

## How the dashboard works
KPI cards sit across the top, with a Key Insight panel on the left. The main visuals are a clustered column chart (outlet by task type), a doughnut of record status, and a horizontal bar chart of average completion time by promoter. The **Area slicer** (Ajah, Alaba, Festac, Ikeja, Ikorodu, Lekki, Marina, Onikan, Surulere, Yaba) filters all of them together.

To explore it, open the workbook, go to **Interactive_Dashboard** and click an area. KPI formulas are in the *cleaned_Dataset* sheet, columns M:N.

## Repository contents
```
├── README.md
├── data/        GlowRoot_Field_Activation.xlsx (cleaned data, pivots, dashboard)
├── assets/      dashboard.png and pivot/chart screenshots
└── docs/
    └── methodology.md   data cleaning, KPI logic, pivot configurations
```
