# MissingValuesExperiment
Small experiment to evaluate which method for missing-value checking is faster. This little experiment is conducted using Python and Pandas.


## Data obtained

| Method              | timeit (us) | time (us) | Absolut errors | Relative errors (%) |
|---------------------|-------------|-----------|----------------|---------------------|
| isnull_any          | 35.305435   | 36.607640 | 1.302205       | 3.688397            |
| isnull_values_sum   | 34.967550   | 38.689070 | 3.721519       | 10.642780           |
| isnull_values_any   | 33.227519   | 32.135324 | 1.092194       | 3.287017            |
| isnull_sum          | 46.771953   | 46.261580 | 0.510373       | 1.091194            |
| isna_any            | 36.021909   | 38.471687 | 2.449778       | 6.800800            |



From the data obtained previously, it's evident that some errors are substantial enough to potentially impact the analysis, especially the 10% discrepancy in the `isnull_values_sum` method. While it's true that more iterations could refine the results, the `isnull_values_any` method stands out with the smallest absolute error and a relatively low relative error. Conversely, the `isnull_sum` method, despite having the smallest absolute error, exhibits the highest runtime values in both cases, indicating potential inefficiency, particularly with larger datasets.

### Key Points:
- **isnull_values_any**: This method demonstrates the smallest absolute and relative errors, suggesting greater consistency and reliability in timing measurements.
- **isnull_values_sum**: While exhibiting large absolute and relative errors, the method's runtime values are notable, especially with the 10% discrepancy, making it less suitable for projects requiring precise timing.
- **isnull_sum**: Although having the smallest error, its runtime values are comparatively larger, implying potential inefficiency, particularly with larger datasets.

Considering both runtime and measurement accuracy, the `isnull_values_any` method emerges as the most consistent and reliable option among those tested. Conversely, the `isnull_values_sum` method may not be suitable for projects where precise timing is critical due to its larger errors and discrepancies between timing methods.
