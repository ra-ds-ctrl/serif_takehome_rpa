# Serif Health DS Takehome Solution - Robert Adelson

## Task
The full task description can be found on the [Data Scientist Take-Home Assignment readme](https://github.com/serif-health/takehome/blob/main/DS_README.md) provided by Matthew. The task was to combine Transparency in Coverage data (payer dataset) with Hospital Price Transparency data (hospital dataset) in a cohesive and unified schema aligning each billing code / payer / hospital combination.

## Inputs
The provided inputs are a payer data sample ([download here](https://mrf.serifhealth.com/public/payer_extract_20250203.csv)) and a hospital data sample ([download here](https://mrf.serifhealth.com/public/hospital_extract_20250203.csv)).

## Approach overview
My general approach is as follows:
- Match hospitals between datasets, using EID and license number (the hospital dataset connects hospital name to EID; I manually identified the hospital name corresponding to each license number in the payer dataset).
- Match payer names between datasets.
- Match plan names as closely as possible between datasets (I got to the point of creating a list of plan names of interest, which were close matches between the two datasets, as well as some much more general "plan names").
- Match codes between datasets (e.g., CPT).
- Although I did not get to it, some matching (and difference calculation, or harmonization in cases of multiple matches) between costs.

## Code
I provide my code as a Jupyter notebook file, since that's the environment in which I developed my solution, and I did not have sufficient time to migrate and test things in a standalone .py file. If you do not have Jupyter Notebook installed, [follow the instructions here](https://jupyter.org/install).

To run the code, on the command line navigate to the directory where you have saved `20250209_takehome_code_rpa.ipynb`. Start up the notebook using the following command: `jupyter notebook 20250209_takehome_code_rpa.ipynb`. Finally, run the cells one by one (or run all via the menu).

## Output
A CSV file with the output is presented. Each row that has at least some data both in columns with the `hospitaldf_` prefix *and* the `payerdf_` prefix shows a match between the two datasets. Each row that has only `hospitaldf_` column data represents a hospital dataset row with no matching payer dataset row. Conversely, each row that has only `payerdf_` column data represents a payer dataset row with no matching hospital dataset row. This CSV is a draft version of a "unified schema", combining the unique schemas of the two input files.
