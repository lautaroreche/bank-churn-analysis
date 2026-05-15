## Findings

- **Observation 1:** the `Surname` column contains identifiable surnames. It was decided to eliminate it in the clean-up phase for protection of personal data and absence of analytical value. This decision is documented to show judgment in the responsible handling of PII (Personally Identifiable Information).
- **Observation 2:** it was decided to eliminate the `RowNumber` column during the clean-up phase due to its lack of analytical value.
- **Observation 3:** the column `Balance` = 0 is distributed suspiciously: 2418 in France, 1199 in Spain, and 0 in Germany. Such an uneven distribution suggests methodological inconsistency in how the data was loaded across countries, or a different business rule in Germany (e.g. mandatory minimum balance). This affects any balance-based analysis and should be treated with caution.
- **Observation 4:** customers with `Balance`= 0 have a churn rate of 13.8%, below the global average (20.4%). This contradicts the initial hypothesis that an empty balance indicates disengagement. Alternative scenario: the `Balance`= 0 segment is concentrated in France and Spain (Germany does not contribute customers to this group), so the result may be affected by geographical composition rather than by the balance sheet itself. Pending analysis: compare `Balance`= 0 churn rate vs `Balance`> 0 within each country.
- **Observation 5:** the pivot total shows 9998 records instead of the expected 10000. To investigate during data quality checks.


