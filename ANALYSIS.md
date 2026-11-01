# Analysis — Excel Sales Tracker (Sample Data)

**Sample data.** Every figure below was computed in Python from
`sales_data.csv` in this folder (25 transactions, Jan–Mar 2026) — the same
file that feeds the workbook's `Data` sheet — using the workbook's own
definitions from `formulas.md`: revenue counts only completed orders that
were not returned, and line total is quantity × unit price. It is
practice data; no real company sales are used.

## Business questions

1. What did the quarter actually net, month by month?
2. Which region and category carry the sales?
3. What explains the February dip?
4. Where do returns hit?

## Key findings

1. **The quarter nets $1,870.62, and January did the heavy lifting.**
   Net revenue by month: January $776.37 (9 orders), February $460.86
   (−40.6% month over month), March $633.39 (+37.4%). March's recovery
   was quality, not just volume — its average order value was the
   quarter's best at $90.48, vs. $76.81 in February.
2. **Electronics is half the business.** Electronics produced $956.77 —
   51.1% of net revenue — ahead of Clothing ($471.00, 25.2%) and Home
   ($442.85, 23.7%). One product, Wireless Headphones, accounts for
   $479.94 of net revenue (25.7%) on just 6 units sold.
3. **West leads the regions, but no region dominates.** West brought in
   $584.35 (31.2%), followed by Midwest ($455.86, 24.4%), East ($435.46,
   23.3%), and South ($394.95, 21.1% on only 3 net orders — South's
   per-order value is actually strong; it simply has fewer orders).
4. **February's dip was partly operational, not just demand.** February
   had 8 raw orders vs. January's 10 — but $95.00 of completed February
   sales was returned (Running Shoes) and a $119.00 Winter Jacket order
   was cancelled outright. Demand fell *and* two orders' worth of value
   leaked out after the sale.
5. **Returns are small in count, real in dollars.** 2 of 24 completed
   lines were returned (8.3%), worth $184.95 — 9.0% of the $2,055.57
   gross completed revenue. Both returns were mid-to-high priced items
   (Coffee Maker $89.95, Running Shoes $95.00), not cheap add-ons.

## What this means

With only 25 sample transactions, none of this is proof of a trend — but
the shape is the one worth watching: revenue concentrated in one
category and one product, a month whose "weakness" was partly returns
and a cancellation rather than traffic, and a region (South) that looks
small only because of order count. These are exactly the patterns the
tracker's Summary, Pivots, and Checks sheets exist to surface each week.

## Recommendations

1. **Protect the headphone supply and placement.** A single product at
   25.7% of net revenue is a concentration risk; keep it in stock and
   use it as the anchor for Electronics promotions.
2. **Treat cancellations and returns as reported metrics, not noise.**
   Add the cancelled-order value and returned value as lines on the
   Summary sheet so a February-style dip is explained the week it
   happens, not reconstructed later.
3. **Grow South order count.** South's revenue per order is competitive;
   the gap is volume (3 net orders vs. 7 each for West and East). A
   region-level order-count target would show whether outreach there is
   working.
4. **Look at the two returned products.** Coffee Maker and Running Shoes
   returns cost $184.95; check the product descriptions and sizing/fit
   information for both before assuming the returns are random.
5. **Keep the reconciliation check non-negotiable.** Every figure above
   was reproducible from the raw CSV because the workbook's numbers are
   formula-driven and tied out — keep the Checks sheet gate before any
   version of this report is shared.
