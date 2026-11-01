# Excel Sales Tracker

> **Key finding:** Electronics drive 51.1% of net revenue; February dipped −40.6% month over month before March recovered +37.4%. Full write-up: [ANALYSIS.md](ANALYSIS.md).

A workbook design for tracking weekly retail sales: one raw data sheet,
formula-driven summaries, and pivot tables for month, region, and product
views — the kind of tracker used to keep recurring sales reporting accurate
without re-doing the math by hand every week.

All data is sample/practice data created for portfolio purposes. No real
company data is used anywhere in this project.

## The question it answers

How are sales tracking by month, region, and product — and does every
reported total actually tie back to the raw transactions?

## Workbook design

| Sheet | Purpose |
|---|---|
| `Data` | Raw transactions, one row per order line (the same layout as `sales_data.csv` in this folder) |
| `Summary` | Formula-driven totals: revenue by month, region, and category using SUMIFS |
| `Lookups` | Product and region reference tables joined onto the data with XLOOKUP |
| `Pivots` | Pivot tables for month × region and category × month summaries |
| `Checks` | Reconciliation checks: summary totals vs. raw-data totals, flagged in red if they differ |

## What was done

- Kept the raw data untouched except for documented cleaning, so every
  summary can be traced back to a source row.
- Built all headline numbers with live formulas (see `formulas.md`) rather
  than typed-in values, so new weeks of data flow through automatically.
- Added conditional checks that compare pivot/formula totals against a
  direct total of the raw data — the same discrepancy check used in
  recurring operational reporting.
- Formatted currency and percentages consistently, and froze the header
  row with filters on for review.

## Skills shown

- Excel formulas: SUMIFS, COUNTIFS, XLOOKUP, INDEX-MATCH, IFERROR
- Pivot tables with grouped dates and calculated summaries
- Conditional formatting for reconciliation flags
- Data validation habits: totals must tie out before the file is shared

## Files

- `README.md` — this file
- `sales_data.csv` — sample transaction data in the exact layout of the `Data` sheet
- `formulas.md` — the exact formulas used in the workbook and what each one computes
- `ANALYSIS.md` — business analysis computed from `sales_data.csv`: headline results, findings, and recommendations
