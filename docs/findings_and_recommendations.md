## Findings

- **Observation 1:** the `Surname` column contains identifiable surnames. It was decided to eliminate it in the clean-up phase for protection of personal data and absence of analytical value. This decision is documented to show judgment in the responsible handling of PII (Personally Identifiable Information).
- **Observation 2:** it was decided to eliminate the `RowNumber` column during the clean-up phase due to its lack of analytical value.
- **Observation 3:** the column `Balance` = 0 is distributed suspiciously: 2418 in France, 1199 in Spain, and 0 in Germany. Such an uneven distribution suggests methodological inconsistency in how the data was loaded across countries, or a different business rule in Germany (e.g. mandatory minimum balance). This affects any balance-based analysis and should be treated with caution.
- **Observation 4:** customers with `Balance`= 0 have a churn rate of 13.8%, below the global average (20.4%). This contradicts the initial hypothesis that an empty balance indicates disengagement. Alternative scenario: the `Balance`= 0 segment is concentrated in France and Spain (Germany does not contribute customers to this group), so the result may be affected by geographical composition rather than by the balance sheet itself. Pending analysis: compare `Balance`= 0 churn rate vs `Balance`> 0 within each country.
- **Observation 5:** the pivot total shows 9998 records instead of the expected 10000. To investigate during data quality checks.
- **Observation 6:** no null values found across the 18 columns. Dataset is complete in terms of missing data.
- **Observation 7:** no duplicate `CustomerId` values found. Each row represents a unique customer.
- **Observation 8:** the `Balance` column shows mean (76486) below median (97198), indicating a left-skewed distribution caused by ~3,600 zero-balance customers. Any analysis using mean balance must account for this skew or filter zeros depending on the question.
- **Observation 9:** the `EstimatedSalary` column shows mean and median nearly identical (~100000) and a minimum value of 11.58, which is unrealistic for annual income. The distribution appears uniform rather than reflecting real-world salary patterns.

