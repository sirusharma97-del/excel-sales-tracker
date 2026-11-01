# Formulas used in the Excel Sales Tracker

Column layout on the `Data` sheet: A = Order ID, B = Order Date,
C = Customer ID, D = Region, E = Category, F = Product, G = Quantity,
H = Unit Price, I = Line Total, J = Status, K = Returned (Y/N).

## Line total (I2, filled down)

```excel
=IF(OR(G2="",H2=""),"",G2*H2)
```

Computes quantity × unit price for each row, and leaves the cell blank
instead of showing 0 when quantity or price is missing.

## Revenue for one month (Summary sheet)

```excel
=SUMIFS(Data!$I:$I, Data!$B:$B, ">="&DATE(2026,1,1), Data!$B:$B, "<"&DATE(2026,2,1), Data!$J:$J, "completed", Data!$K:$K, "N")
```

Total line revenue for January 2026, counting only completed orders that
were not returned. Change the two DATE values for other months.

## Revenue for one region (Summary sheet)

```excel
=SUMIFS(Data!$I:$I, Data!$D:$D, "West", Data!$J:$J, "completed", Data!$K:$K, "N")
```

## Order count for one region

```excel
=COUNTIFS(Data!$D:$D, "West", Data!$J:$J, "completed")
```

## Average order value for the month

```excel
=IFERROR(month_revenue_cell / month_order_count_cell, 0)
```

Divides the month's SUMIFS revenue by its COUNTIFS order count; returns 0
instead of #DIV/0! in a month with no orders.

## Product category lookup (helper column on Data, or Lookups sheet)

```excel
=XLOOKUP(F2, Products!$A:$A, Products!$B:$B, "Check product list")
```

Pulls each product's category from the Products reference table; if the
product is missing from the table it shows "Check product list" instead of
an error, which doubles as a data-quality flag.

Older-Excel equivalent with INDEX-MATCH:

```excel
=IFERROR(INDEX(Products!$B:$B, MATCH(F2, Products!$A:$A, 0)), "Check product list")
```

## Month-over-month change

```excel
=IFERROR((B3-B2)/B2, "")
```

Percentage change between this month's revenue cell (B3) and last month's
(B2) on the Summary sheet; blank for the first month.

## Reconciliation check (Checks sheet)

```excel
=IF(ROUND(Summary_total - SUM(Data!$I:$I), 2) = 0, "OK", "DIFFERENCE — investigate")
```

Compares the sum of all Summary-sheet figures against a direct total of
the raw data. Conditional formatting turns the cell red on anything other
than "OK" — the summary is not shared until this check passes.

## Pivot table summaries (no formulas)

- **Month × Region:** Rows = Order Date grouped by Month, Columns =
  Region, Values = Sum of Line Total (filtered to Status = completed,
  Returned = N).
- **Category × Month:** Rows = Category, Columns = Month, Values = Sum of
  Line Total and Count of Order ID.
- Both pivots are cross-checked against the SUMIFS figures on the Checks
  sheet before use.
