# Online Retail Store Analysis

Sales analysis of a UK-based online retailer's transactions (541,909 rows, 1 Dec 2010 to 9 Dec 2011) with pandas. A practice project built around a business scenario, with a Power BI file included.

**Notebook:** `Online Retail.ipynb` (data: `Online Retail.xlsx`)

**Power BI file:** `Online Retail Project.pbix` (built before the cleaning below was corrected, so its numbers can differ from the notebook; an earlier online copy was unavailable when checked)

The scenario asks which countries and products drive revenue, to plan for next year. The scenario says the UK is not needed in the country analysis, so the country questions exclude it. All amounts are in GBP.

## Cleaning

- Dropped 5,268 exact duplicate rows.
- Excluded cancellations, negative quantities and zero-price rows (about 11,800 rows), so the analysis is gross sales: 524,878 sales rows, 10.64 million GBP.
- Kept single-unit sales and rows without a CustomerID (about 25% of rows), since the questions do not need the customer.

## Findings

- **Top countries (excluding the UK):** Netherlands, EIRE, Germany, France and Australia, by both quantity sold and revenue. The median country brings in about 13.5 thousand GBP, and the UK alone is about 9.0 million of the 10.6 million total.
- **Trend:** revenue is flat through the first half of 2011 and climbs from September, peaking in November 2011 at about 1.5 million GBP. December 2011 is only 9 days of data.
- **Products:** the top revenue codes include a postage fee (DOT) and products such as the Regency cakestand (22423) and the white hanging heart t-light holder (85123A). Code 23843 ranks high only because of the outlier order noted below.
- **Quantity and revenue per product:** positively related (Spearman about 0.87).

## Limitations

- Revenue is gross sales. Cancellations (about GBP 0.89M, 8.4% of gross) are excluded, not netted, so net sales are about GBP 9.75M.
- One order of 80,995 units (invoice 581483, GBP 168,470, 1.6% of gross) was cancelled 12 minutes later but still counts as a gross sale. Without it, gross sales are GBP 10.47M and product code 23843 drops out of the top products.
- About GBP 0.38M (3.6%) of gross comes from non-product codes such as postage (DOT, POST), manual entries and Amazon fees.
- One year of data cannot confirm a repeating seasonal pattern.
