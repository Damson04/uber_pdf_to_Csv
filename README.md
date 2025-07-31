# uber_pdf_to_Csv

This notebook documents the process of extracting, cleaning, and analyzing Uber transaction data from PDF statements for the year 2024 and 2025. Here's a step-by-step breakdown of what was done:

---

## 1. Initial Setup and Data Extraction

Imported necessary libraries including:
- `os` for file operations
- `tabula` and `pdfplumber` for PDF extraction
- `re` for regular expressions
- `pandas` and `numpy` for data manipulation
- `matplotlib` and `seaborn` for visualization

---

## 2. PDF Processing

Processed multiple PDF files from the Uber statements directory for 2024:
- Used `pdfplumber` to extract text from each PDF page
- Applied a regular expression pattern to parse transaction data including:
  - Processed date
  - Event type (UberX, Tips, etc.)
  - Earnings amount
  - Refunds & expenses
  - Balance

---

## 3. Data Cleaning and Transformation

Created a DataFrame (`df_2024`) from the extracted data:
- Cleaned currency values by:
  - Removing "CA$" prefixes
  - Removing commas from numbers
  - Converting to float data type
- Renamed columns for clarity:
  - `processed` → `Processed_Date`
  - `event` → `Event`
  - `earnings` → `Your earnings`
  - `refunds` → `Refunds & Expenses`
  - `balance` → `Balance`

---

## 4. Date Handling

- Added year information (2024) to the date strings
- Created a new column `Processed_Date` with proper datetime format using `pd.to_datetime`
- Dropped the original `source_file` column as it was no longer needed

---

## 5. Data Exploration

- Examined the structure of the data with `df_2024.info()`
- Viewed the first and last few rows with `head()` and `tail()`
- The final dataset contains 3,410 transactions across 6 columns

---

## Key Observations

- The data includes different types of Uber events (UberX, Tips, etc.)
- Some transactions have null values in the "Refunds & Expenses" column was successfully converted due to `fillna`
- Dates were successfully converted to datetime format for time-based analysis
- All monetary values were properly converted to numeric format
