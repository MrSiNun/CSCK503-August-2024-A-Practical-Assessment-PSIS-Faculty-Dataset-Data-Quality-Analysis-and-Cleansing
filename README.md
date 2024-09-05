# MLMidModuleAssignment

Here is a potential README file for the GitHub project based on the contents of your provided report:

---

# SIS Faculty Dataset Data Quality Analysis and Cleansing

## Project Overview

This project focuses on the **data quality analysis and cleansing** of a **Student Information System (SIS) faculty dataset**, which serves as a precursor to machine learning activities. The main goal is to ensure the dataset is clean and ready for use in a machine learning pipeline, primarily by addressing data quality issues such as missing values, inconsistent formatting, and redundant data.

## Dataset

The dataset contains faculty information from an SIS, including columns such as faculty ID, Last Working Date (LWD), Highest Qualification, Location, and Title, among others. The dataset was found to have various data quality issues which were rectified during this project.

## Key Data Quality Issues

1. **Missing Values:**
   - The `ID` column had placeholder values ('0') representing missing entries.
   - The `LWD` column had numerous missing values.

2. **Inconsistent Data:**
   - Inconsistent naming conventions in the `Highest Qualification` column (e.g., "Master of Science" vs. "M.Sc.").
   - The `Join Date` column contained newline characters, which needed standardization.

3. **Redundant Data:**
   - Categorical columns such as `Location` and `Title` had been one-hot encoded. These encoded columns needed to be validated for accuracy.

4. **Unstructured Text:**
   - Columns such as `Courses Taught` contained long text values that may require transformation for machine learning purposes.

## Data Cleansing Process

The following steps were implemented to improve data quality:

- **Handling Missing Values:**
  - Rows with an `ID` of '0' were removed.
  - Missing values in the `LWD` column were filled with "Not Available."

- **Standardizing Data:**
  - Removed newline characters from the `Join Date` column.
  - Standardized inconsistent qualification names (e.g., converting "Master of Science" to "M.Sc.").

- **Validating Categorical Data:**
  - One-hot encoding of `Location` and `Title` columns was validated and confirmed to be accurate.

## Python Implementation

Here are the key Python functions used in the data cleansing process:

```python
# Drop rows with invalid IDs
df_cleaned = df[df["ID"] != "0"]

# Fill missing values in the 'LWD' column
df_cleaned["LWD"] = df_cleaned["LWD"].fillna("Not Available")

# Clean 'Join Date' column and standardize qualifications
df_cleaned["Join Date"] = df_cleaned["Join\nDate"].str.replace("\n", "")
df_cleaned["Highest Qualification"] = df_cleaned["Highest Qualification"].str.lower().str.replace("master", "M.Sc.")
```

## Conclusions

The data cleansing process resolved key data quality issues, including missing values, inconsistent formatting, and unstructured text. The cleaned dataset is now consistent and ready for use in machine learning models.

## Repository Structure

- **`SIS_Faculty-List.csv`**: Original dataset before cleansing.
- **`cleaned_sis_faculty_data.csv`**: Cleaned dataset ready for machine learning.
- **`Data Quality Analysis.ipynb`**: Jupyter Notebook containing the data cleansing code and analysis.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/MrSiNun/MLMidModuleAssignment.git
   ```
2. Run the Jupyter Notebook to see the data cleansing process step-by-step.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

This template will help provide an overview of the project and guide users on how to use it. Let me know if you need any changes or further details!
