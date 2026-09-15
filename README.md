# Sales-Tracker-Google-Sheet
A lightweight sales tracker that auto-calculates daily, weekly, and monthly totals from raw sales entries  built for the Veda Technology Data Analytics internship task .
# Objective
Practice structuring a spreadsheet for ongoing data entry and automatic aggregation, without relying on manual recalculation.
# Structure
The workbook is split into six sheets, separating raw entry from computed output:
# Sheet	Purpose
Raw Data	Single entry point for all sales transactions (Date, Product, Category, Quantity, Unit Price, Amount, Salesperson). Amount is auto-calculated via formula — never entered manually.
Daily Summary	Per-day transaction count, quantity, total sales, and average sale, pulled with SUMIFS/COUNTIFS.
Weekly Summary	Monday–Sunday rollups using date-range SUMIFS.
Monthly Summary	Month-wise totals using SUMIFS with EDATE for month boundaries.
Dashboard	At-a-glance totals — overall transactions, quantity, sales, and average sale.
Lists	Dropdown source lists (Product, Category, Salesperson) used for data validation on the Raw Data sheet.
# Approach
•	Single source of truth: all formulas reference Raw Data only, so totals update automatically the moment a new row is entered — no manual refresh or copy-paste.
•	Error-safe formulas: the Amount column uses IF(OR(...),"",...) so blank or incomplete rows don't throw errors or get miscounted.
•	Data validation: dropdowns (sourced from the Lists sheet) constrain Product, Category, and Salesperson entries, reducing typos and keeping SUMIFS matches reliable.
•	Separation of concerns: raw entry is isolated from computed summaries, so formulas can't be accidentally overwritten by someone entering data.
# How totals were verified
Sample transactions were manually summed for a few individual days and one full week, then cross-checked against the Daily and Weekly Summary sheet outputs to confirm the SUMIFS logic matched a manual calculation before scaling to the full dataset.
Interview questions — my answers
How would you design a spreadsheet so non-technical staff can enter data safely? Keep one dedicated entry sheet with dropdown-validated columns (via Data Validation, sourced from a Lists sheet) so staff pick from fixed options instead of free-typing. Lock or separate all formula-driven sheets from the entry sheet so a typo or accidental drag can't overwrite a calculation.
What's the risk of mixing raw data with formulas on the same tab? Formulas can get overwritten, shifted, or deleted the moment someone enters a new row in the wrong place — breaking totals silently, since a formula error may not always throw a visible warning. Keeping raw entries and calculations on separate tabs means new data flows in safely while the summary logic stays untouched.
# Tools
Google Sheets (formulas: SUMIFS, COUNTIFS, EDATE, IFERROR, IF/OR; Data Validation for dropdowns)

