# Data Cleaning and Preprocessing

This repository contains Python scripts to clean and preprocess Starrydata2 data, specifically for thermal conductivity analysis.

## Data Processing Pipeline

The data processing consists of several steps:

1. **Initial Data Import:** Data is imported from '20230112_interpolated_data.csv'. The script keeps only specific columns: 'composition', 'sampleinfo', 'Temperature', 'Thermal conductivity', and 'total thermal conductivity'.

2. **Temperature Filter:** The script filters data based on the 'Temperature' column, keeping only rows with temperatures between 300 and 1000.

3. **Merging Conductivity Columns:** The 'Thermal conductivity' and 'total thermal conductivity' columns are merged into a new column, 'Merged conductivity'. If both columns contain different non-empty, non-NaN values, the maximum of the two is used. If either column is empty or NaN, the non-empty, non-NaN value is used.

4. **Removing Unnecessary Columns:** The script drops the original 'Thermal conductivity' and 'total thermal conductivity' columns.

5. **Handling Missing Conductivity Values:** The script removes rows with missing 'Merged conductivity' values.

6. **Removing Invalid Conductivity Values:** Rows with empty strings or non-positive values in the 'Merged conductivity' column are removed.

7. **Removing Invalid Compositions:** Rows with invalid compositions (NaN, non-string, or empty string) are removed.

8. **Extracting Sample Category:** A new 'Category' column is created by extracting category information from the 'sampleinfo' column.

9. **Filtering Categories:** The script removes rows belonging to certain categories specified in the 'categories_to_remove' list.

10. **Cleaning 'composition' Column:** The script cleans the 'composition' column by removing spaces, special symbols, rows that satisfy a certain condition, and unbalanced parentheses.

11. **Assigning Coefficients of 1:** The script assigns a coefficient of 1 to elements that are followed by another element or parentheses, and to closing parentheses followed by an opening parenthesis, an element, or the end of the string.

12. **Validating Compositions:** Compositions are validated based on a list of elements. All elements in the composition must be in the provided list, and all coefficients and multipliers must be valid non-zero numbers. Invalid compositions are replaced with NaN.

13. **Expanding Brackets:** Brackets in the compositions are expanded. For example, 'Ba(OH)2' becomes 'BaO2H2'.

14. **Merging Duplicate Elements:** Duplicate elements in the compositions are merged by summing their counts.

15. **Filtering Conductivity Values:** Rows with 'Merged conductivity' values greater than 500 are removed.

16. **Feature Calculation:** The script converts the composition string into a pymatgen Composition object and calculates Magpie features from this Composition object.

17. **Binning Conductivity Values:** The 'Merged conductivity' values are binned into three groups using specified bins and labels. The binning results are stored in a new 'class' column.

18. **Extracting Main Elements:** The script extracts the two main elements (the ones with the highest counts) from each composition and stores them in a new 'main_elements' column.

19. **Removing Specific Compounds:** Rows containing all of the elements 'U', 'O', 'F', and 'P' are removed to exclude certain unparsable compounds.

20. **Final Data Export:** The script exports the final cleaned and processed data to two CSV files: 'training_data_with_composition.csv' (including the 'new_composition' column) and 'training_data.csv' (excluding the 'new_composition' column).

Please refer to the Python scripts for detailed implementation of each step.
