# 🧠 Marketing Data Aggregation and Feature Engineering Pipeline

This Python script processes and aggregates multiple raw datasets related to car sales and marketing in Sweden, transforming them into a **weekly-level dataset** ready for modeling (e.g. Marketing Mix Modeling). It handles **data cleaning**, **region standardization**, **date filtering**, **pivoting**, and **feature engineering** (like holidays and Ramadan flags).

---

## 📁 Input Files

Place the following datasets in the appropriate `../Data/` directory relative to the script:

| File Name                         | Description                                 | Format  |
|----------------------------------|---------------------------------------------|---------|
| `simulated_car_transfer.xlsx`    | Ownership transfer data per region          | Excel   |
| `CPI.xlsx`                       | Consumer Price Index (CPI) for Sweden       | Excel   |
| `Försäljning Personbil.csv`     | Car sales data per region                   | CSV     |
| `EMMAUtskick.csv`                | Email impression data per region            | CSV     |
| `MMM cleaned 2503.csv`           | Marketing spend and impressions by channel  | CSV     |
| `Bränslepriser.xlsx`             | Gasoline/fuel prices                        | Excel   |

---

## 🛠️ Features

- **Standardizes region names** using a mapping to official Swedish regions.
- Cleans and converts date and numeric values (supports both `,` and `.` decimals).
- Filters data by a fixed date range (`2022-01-01` to `2025-03-24`).
- **Automatically handles holidays and Ramadan** (based on known dates).
- Aggregates data to daily and weekly levels.
- Pivots marketing data into separate cost/impression columns per channel.
- Fills missing values intelligently (0 for sums, forward-fill for indicators).
- Saves final output to Excel (`aggregated_weekly_data.xlsx`).

---

## 🧾 Output

- `aggregated_weekly_data.xlsx`: Cleaned, feature-enriched, and aggregated data at weekly frequency (Monday-aligned).

---

## 📦 Dependencies

Install requirements via pip:

```bash
pip install pandas numpy holidays openpyxl
```

## ⚙️ Configuration
- Modify FILE_NAMES in the script if your files are located elsewhere.
- Update the VALID_REGIONS list or STD_COL_MAPPINGS dict for new regions/column headers.

## 🧪 Sample Features in Output

| Feature             | Description                                  |
|---------------------|----------------------------------------------|
| `Ownership_Transfers` | Daily or weekly ownership transfers          |
| `Sales`              | Number of car sales                          |
| `Email_Impressions`  | Email marketing impressions                  |
| `SEM_Cost`           | Cost of SEM channel marketing                |
| `SEM_Impressions`    | Impressions from SEM                         |
| `CPI`                | Consumer Price Index                         |
| `Gas_Price`          | National fuel price                          |
| `Is_Holiday`         | Binary flag: was the day a Swedish holiday? |
| `Is_Ramadan`         | Binary flag: was the day during Ramadan?     |


## ✅ Status Messages
The script prints informative messages during execution, including:

- File loading summaries
- Column cleaning results
- Aggregation stats
- Any missing or malformed entries
- Output path of the saved results


