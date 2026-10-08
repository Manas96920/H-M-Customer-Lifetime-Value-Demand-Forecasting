# H&M Customer Lifetime Value + Demand Forecasting

Two complementary Metabase dashboards connect **customer value and retention** with **demand and inventory planning**. This public repository presents dashboard previews, KPI interpretation and business decisions from an independent historical analytics portfolio project.

**12 business tabs · 69 saved questions · Python · PostgreSQL · Metabase**

[CLV dashboard gallery](dashboards/customer-lifetime-value.md) · [Demand dashboard gallery](dashboards/demand-inventory-planning.md) · [Private implementation](https://github.com/Manas96920/H-M-CLV-DF) · [Business enquiries](mailto:manasranjan96920@gmail.com)

## H&M CLV — Business Overview

The CLV dashboard shows which existing customers contribute value, how customer groups differ, where retention opportunities lie, and how reliably future revenue can be estimated. The model uses purchase occasions, BG/NBD and monetary estimates with chronological validation; the 12-month result is discounted future **revenue**, not profit.

![H&M CLV overview](assets/dashboards/clv-overview.jpg)

| Tab | What it represents | Business viewpoint |
|---|---|---|
| [Overview](dashboards/customer-lifetime-value.md#overview) | Observed buyers, discounted 12-month revenue CLV, next-90-day revenue, repeat buyers, high-value lapsed buyers, predicted tiers, monthly sales and value concentration. | Prioritize customer-value opportunities and monitor concentration. |
| [Customer segments](dashboards/customer-lifetime-value.md#customer-segments) | Age, newsletter preference, membership, source FN/Active flags, frequency, recency, tenure, cross-segments and the complete segment KPI explorer. | Compare descriptive groups and design controlled CRM tests; preference is not newsletter send frequency. |
| [Retention & finance](dashboards/customer-lifetime-value.md#retention--finance) | Suggested retention actions, margin/uplift budget scenarios, discount/demand sensitivity and historical-to-future value migration. | Compare possible campaign budgets under explicit assumptions; these are not measured campaign ROI. |
| [Merchandising & cohorts](dashboards/customer-lifetime-value.md#merchandising--cohorts) | Category sales, channel activity, cohort retention, category affinity and complete cohort activity. | Connect assortment and capacity decisions with customer continuity; overlapping category buyers are not additive. |
| [Model quality](dashboards/customer-lifetime-value.md#model-quality) | Candidate comparison, selected-model metrics, holdout targeting, full validation/test results and limitations. | Assess forecast reliability and targeting concentration before spending on incentives. |
| [Definitions & data](dashboards/customer-lifetime-value.md#definitions--data) | Portfolio KPI tables, formula dictionary and missing operational/commercial inputs. | Align KPI interpretation and plan the next data collection steps. |

### CLV findings

| KPI / finding | Result | Interpretation |
|---|---:|---|
| Observed buyers | 1,362,281 | Customers with recorded purchases; registry-only customers are excluded from buyer modeling. |
| Repeat buyers | 67.12% | Purchases on more than one distinct calendar day. |
| Discounted 12-month revenue CLV | 401,277.44 original H&M price units | Finite 365-day revenue projection at an assumed 10% annual discount. |
| Next 90-day revenue forecast | 103,605.99 original H&M price units | Existing observed buyers only; future acquisitions excluded. |
| High historical-value buyers lapsed 90+ days | 65,395 | A review population for controlled, low-cost reactivation tests. |
| High future-value tier share | 68.36% of projected CLV | Roughly the top 20% of buyers concentrate forecast value. |
| Test top-20% targeting capture | 63.90% of subsequent eligible-buyer revenue | 3.20× concentration lift; this is not causal campaign uplift. |
| Test revenue MAE improvement | 14.47% versus recent spending | Benchmark comparison for 90-day existing-buyer revenue. |
| Test WAPE / revenue bias | 103.01% / +11.20% | Individual forecasts are noisy; use targeting and portfolio context alongside errors. |

## H&M Demand — Inventory Planning

The demand dashboard evaluates future purchased-item volume, reconciles category/channel forecasts, exposes seasonality and assortment priorities, and translates forecast uncertainty into explicit inventory policy scenarios. Eight candidate models are compared through rolling validation; the final eight-week test is held out from model selection.

![H&M demand overview](assets/dashboards/demand-executive-overview.jpg)

| Tab | What it represents | Business viewpoint |
|---|---|---|
| [Executive overview](dashboards/demand-inventory-planning.md#executive-overview) | Four/eight-week volume forecasts, WAPE and bias, demand history, scenario bands, business findings and the complete KPI table. | Agree category capacity and planner review priorities. |
| [Forecast accuracy](dashboards/demand-inventory-planning.md#forecast-accuracy) | Holdout actuals vs forecast, benchmarks, category errors, selected leaf models, validation folds, category holdout explorer, fit exceptions and portfolio/channel accuracy. | Choose defensible models and detect aggregate errors that hide category weaknesses. |
| [Category and channel](dashboards/demand-inventory-planning.md#category-and-channel) | Category forecast volume, category KPIs, uncertainty explorer, weekly category selector and channel mix. | Allocate category/channel capacity and investigate demand shifts. |
| [Seasonality and assortment](dashboards/demand-inventory-planning.md#seasonality-and-assortment) | Complete-month demand, weekday patterns, month/category intensity, SKU ABC/XYZ, top SKUs and lifecycle. | Prioritize stable high-volume products and review erratic, inactive or newly observed lines. |
| [Inventory planning](dashboards/demand-inventory-planning.md#inventory-planning) | 228 lead/review/quantile policies, illustrative stock targets, actual-input readiness, planner exceptions and category CLV context. | Compare demand protection periods and calculate shortfalls only after actual stock inputs are supplied. |
| [Definitions and data](dashboards/demand-inventory-planning.md#definitions-and-data) | Source limitations, inventory assumptions, data requirements and KPI formulas. | Align units and collect stock, lead time, cost, availability and current transactions. |

### Demand and inventory findings

| KPI / finding | Result | Interpretation |
|---|---:|---|
| Complete weekly history | 104 weeks | Monday–Sunday observations through 2020-09-20. |
| Forecast aggregation | 36 category/channel series → 19 categories → portfolio | Category and channel totals reconcile. |
| Four-week forecast | 1,226,243 sold-item rows | Item-row proxy; explicit physical quantity is unavailable. |
| Eight-week forecast | 2,180,545 sold-item rows | Historical period 2020-09-21 to 2020-11-15. |
| Eight-week holdout WAPE | 6.75% | Test demand error at portfolio level. |
| Four-week-average baseline WAPE | 13.00% | Selected approach reduces relative test WAPE by 48.02%. |
| Test bias | −2.59% | Aggregate underforecast on the historical test. |
| Garment Upper body forecast share | 49.81% | Concentration requires category-specific accuracy review. |
| Categories flagged for planner review | 12 | Undefined or >50% WAPE, or absolute bias >20%; a heuristic, not an order trigger. |
| Inventory policy scenarios | 228 | 1/2/4-week lead × 1/2-week review × 90th/95th nominal demand percentile, across 19 categories. |

The inventory view shows demand protection targets and empirical buffers. Suggested orders remain blank until actual on-hand, on-order and backorder inputs are supplied. MOQ, case-pack and unit-cost inputs support purchasing calculations once available; category targets still need SKU/size/location allocation.

## Explore every tab

The two galleries display **all six tabs of each dashboard**, with multiple captured views where a tab extends below the screen. Wide tables contain additional columns available inside the original Metabase questions.

<details>
<summary>CLV — Overview</summary>

Customer value and revenue concentration. Prioritize customer-value opportunities and monitor concentration.

![CLV — Overview](assets/dashboards/clv-overview.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>CLV — Customer segments</summary>

Who buys and how they behave. Compare descriptive groups and design controlled CRM tests; preference is not newsletter send frequency.

![CLV — Customer segments](assets/dashboards/clv-customer-segments.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>CLV — Retention & finance</summary>

Retention priorities and financial assumptions. Compare possible campaign budgets under explicit assumptions; these are not measured campaign ROI.

![CLV — Retention & finance](assets/dashboards/clv-retention-finance.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>CLV — Merchandising & cohorts</summary>

Category affinity and customer continuity. Connect assortment and capacity decisions with customer continuity; overlapping category buyers are not additive.

![CLV — Merchandising & cohorts](assets/dashboards/clv-merchandising-cohorts.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>CLV — Model quality</summary>

Forecast evaluation and targeting quality. Assess forecast reliability and targeting concentration before spending on incentives.

![CLV — Model quality](assets/dashboards/clv-model-quality.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>CLV — Definitions & data</summary>

KPI meaning and collection needs. Align KPI interpretation and plan the next data collection steps.

![CLV — Definitions & data](assets/dashboards/clv-definitions-data.jpg)

[See every captured view](dashboards/customer-lifetime-value.md)

</details>

<details>
<summary>Demand — Executive overview</summary>

Demand planning at portfolio level. Agree category capacity and planner review priorities.

![Demand — Executive overview](assets/dashboards/demand-executive-overview.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

<details>
<summary>Demand — Forecast accuracy</summary>

How well demand forecasts performed. Choose defensible models and detect aggregate errors that hide category weaknesses.

![Demand — Forecast accuracy](assets/dashboards/demand-forecast-accuracy.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

<details>
<summary>Demand — Category and channel</summary>

Where future volume is concentrated. Allocate category/channel capacity and investigate demand shifts.

![Demand — Category and channel](assets/dashboards/demand-category-and-channel.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

<details>
<summary>Demand — Seasonality and assortment</summary>

Calendar patterns and SKU priorities. Prioritize stable high-volume products and review erratic, inactive or newly observed lines.

![Demand — Seasonality and assortment](assets/dashboards/demand-seasonality-and-assortment.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

<details>
<summary>Demand — Inventory planning</summary>

Demand translated into policy scenarios. Compare demand protection periods and calculate shortfalls only after actual stock inputs are supplied.

![Demand — Inventory planning](assets/dashboards/demand-inventory-planning.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

<details>
<summary>Demand — Definitions and data</summary>

Planning assumptions and missing inputs. Align units and collect stock, lead time, cost, availability and current transactions.

![Demand — Definitions and data](assets/dashboards/demand-definitions-and-data.jpg)

[See every captured view](dashboards/demand-inventory-planning.md)

</details>

## Read the results correctly

- Source history runs from **2018-09-20 to 2020-09-22**. CLV is as of 2020-09-22; demand uses complete weeks ending 2020-09-20. This is a historical demonstration, not a current H&M forecast.
- Values remain in **original H&M price units**; no verified currency conversion is applied. CLV is revenue, not net profit or measured campaign ROI.
- CLV customer-level revenue errors and demand portfolio-volume errors concern different targets and cannot be compared directly.
- Customer-days proxy purchase occasions and transaction rows proxy sold items. Orders, verified quantities, returns and availability are missing.
- Age and newsletter preference comparisons are descriptive. Newsletter preference does not measure send/open/click cadence or causal engagement.
- Category customer affinity overlaps across categories. Do not add those customer counts or customer CLV values together.
- Forecast bands use a small, selection-influenced residual sample. They are empirical scenarios, not guaranteed future coverage or supplier service levels.

## Source and implementation

Data source: [H&M Personalized Fashion Recommendations on Kaggle](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data). Dataset access is subject to the [competition rules](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/rules). Raw source data is not distributed here.

The [private **H&M - CLV + DF** repository](https://github.com/Manas96920/H-M-CLV-DF) contains notebooks, Python pipelines, SQL reporting definitions, tests, documentation, dependency versions, compact results and verification evidence. Access requires the owner's authorization; visitors without access may see GitHub's 404 page. Public previews are static screenshots. The local Metabase addresses in the galleries only work with the owner's running instance and are not public dashboard URLs.

GitHub private visibility prevents unauthorised access; authorized users with repository access can still clone or download. There is no GitHub “view-only but cannot clone” setting. See [GitHub repository visibility](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories).

## Business contact

For analytics consulting, dashboard demonstrations or project enquiries, contact **Manas** at **[manasranjan96920@gmail.com](mailto:manasranjan96920@gmail.com)**. Implementation access is reviewed separately and is not granted automatically by an enquiry.

This is an independent portfolio project and is not affiliated with or endorsed by H&M.
