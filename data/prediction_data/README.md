# Data Needed for Prediction

This repository contains two Python scripts to extract specific elemental properties and perform compound-specific calculations.

## melting_points: Extracting Melting Points

The first script, `melting_points.ipynb`, imports all elements from the `pymatgen` library and retrieves their respective melting points. It then filters out metals and exports the final data to a CSV file, `melting_point_metals.csv`.

The script performs the following steps:

1. **Element Import:** All elements are imported from the `pymatgen` library, except for uranium.

2. **Melting Point Extraction:** The melting point is extracted for each element. If a melting point is not available, the script assigns `None`.

3. **DataFrame Preparation:** The script creates a DataFrame with two columns: "Element" and "Melting Point".

4. **Metal Filtering:** The script creates a new DataFrame that contains only metals.

5. **Data Export:** The script exports the final DataFrame to a CSV file, `melting_point_metals.csv`.

## mp_uranium_compounds: Calculating Uranium Density

The second script, `mp_uranium_compounds.ipynb`, uses the Materials Project API to search for uranium compounds, calculate their uranium density, and export the data to a CSV file, `mp_uranium_compounds.csv`.

The script performs the following steps:

1. **API Search:** The script uses the Materials Project API to search for stable uranium compounds and retrieves their formulas and densities.

2. **Uranium Density Calculation:** For each compound, the script calculates the uranium density.

3. **DataFrame Creation:** The script creates a DataFrame with the pretty formula, compound density, and uranium density for each compound.

4. **Data Export:** The script exports the DataFrame to a CSV file, `mp_uranium_compounds.csv`.

Please refer to the individual Python scripts for detailed implementations of each step.
