# Data Dictionary

Source: `data/raw/Customer-Churn-Records.csv` (10000 rows × 18 columns).
Public dataset of European retail banking customers, used for churn analysis.

## Columns

| # | Column | Type | Description | Possible Values / Range | Used in Analysis |
|---|---|---|---|---|---|
| 1 | `RowNumber` | int | Sequential row index from the source file. | 1–10000 | Dropped |
| 2 | `CustomerId` | int | Unique identifier for each customer. Used as a key for joins with the synthetic transactions table. | 8-digit integer | Key only |
| 3 | `Surname` | string | Customer surname. Removed for privacy reasons and because it carries no analytical signal. | Free text | Dropped |
| 4 | `CreditScore` | int | Credit score assigned to the customer. Higher values indicate better creditworthiness. | Integer, typically 350–850 | Yes |
| 5 | `Geography` | string | Country where the customer holds the account. | France, Germany, Spain | Yes |
| 6 | `Gender` | string | Customer gender as recorded by the bank. | Male, Female | Yes |
| 7 | `Age` | int | Customer age in years. | ≥ 18 | Yes |
| 8 | `Tenure` | int | Number of years the customer has held a relationship with the bank. | 0–10 | Yes |
| 9 | `Balance` | float | Current account balance in euros. | ≥ 0 | Yes |
| 10 | `NumOfProducts` | int | Number of bank products held by the customer. | 1–4 | Yes |
| 11 | `HasCrCard` | int | Flag indicating whether the customer holds a credit card with the bank. | 0 = No, 1 = Yes | Yes |
| 12 | `IsActiveMember` | int | Bank-defined activity flag. The exact criteria are not documented in the source dataset and should be treated as a proxy rather than a strict behavioral measure. | 0 = No, 1 = Yes | Yes (with caveat) |
| 13 | `EstimatedSalary` | float | Estimated annual salary of the customer. | ≥ 0 | Yes |
| 14 | `Exited` | int | Indicates whether the customer has left the bank (hard churn). | 0 = No, 1 = Yes | Yes |
| 15 | `Complain` | int | Flag indicating whether the customer contacted the bank with a complaint. | 0 = No, 1 = Yes | Yes |
| 16 | `Satisfaction Score` | int | Customer satisfaction score collected post-interaction. | 1–5 | Yes |
| 17 | `Card Type` | string | Tier of the customer's card product. | DIAMONG, GOLD, SILVER, PLATINUM | Yes |
| 18 | `Point Earned` | int | Loyalty points earned by the customer. | ≥ 0 | Yes |

## Variable Roles

- **Target:** `Exited`
- **Identifiers:** `CustomerId`, `RowNumber`, `Surname`
- **Demographics:** `Geography`, `Gender`, `Age`
- **Relationship depth:** `Tenure`, `NumOfProducts`, `HasCrCard`, `Card Type`
- **Financial:** `CreditScore`, `Balance`, `EstimatedSalary`
- **Engagement:** `IsActiveMember`, `Point Earned`
- **Customer experience:** `Complain`, `Satisfaction Score`

## Notes and Caveats

- The dataset is a **point-in-time snapshot**. It does not capture how variables evolved over time, which is a key limitation for behavioral churn analysis.
- `EstimatedSalary` should be interpreted carefully. Its distribution in this dataset is close to uniform, which is uncommon in real income data and suggests the values are simulated or heavily smoothed.
- `IsActiveMember` is bank-defined and its exact rule is unknown. It is used here as provided, but the analysis does not rely on it as a sole indicator of engagement.
- `Complain` is strongly correlated with `Exited` in this dataset. This relationship is documented during EDA and discussed in the findings, since it materially affects how the service recovery hypothesis can be tested.