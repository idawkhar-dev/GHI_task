# GHI_task
This repo is public as it is a submission for GHI team's selection task

# Problem statement: 
The goal of this task was calculating the impact scores for all drugs (HIV) impacted in the yeat 2015. After reading the supporting documents, I realised that each disease has a seperate impact score formula and all these formulas currently are computed in an excel using formulas. The task was to convert these formulas into a Python code. I tried implementing a different approach but decided to move ahead with a row-wise calculation approach. 

# Current Approach:
The final approach I implemented directly replicates the Excel formulas used in the HIV2015 dataset. For each drug and country, it dynamically searches the regimen tables, identifies which regimens contain the drug, and calculates the impact score using adult and child DALYs, coverage factors, regimen proportions, and efficacy values. This method ensures that the computed scores match the original Excel results. 

# Alternate Approach explored:
The alternative “drug impact matrix” approach aimed to precompute a matrix of drug-regimen contributions and then aggregate these for each country. While conceptually faster for multiple drugs, it introduced alignment and indexing complexities that made debugging difficult and increased the risk of discrepancies with the Excel outputs.

Important calculations:

1. Regimen-Drug Matrix (R):

Rows: Each regimen (both first-line and second-line).
Columns: Each drug (3TC, AZT, EFV, etc.)
R(i,j) = 1 if drug (j) is present in regimen (i) , else 0 

2. Impact Vector (X):
each entry X(i) represents the calculated contribution of regimen (i) to impact. The formula per regime remains the same as Excel logic.

3. Drug Impact Vector (D)
Multiply the transpose of the regimen-drug matrix by the regimen impact vector. Each D(j) gives the total impact score for drug(j) across all regimens.

4. Normalization
The formula for the normalization is as same as used in Excel file.

# Future Scope: 
I had limited time and resources to make this soultion work. Thus,if given the chance I would like to explore in more detail to make this mode computationally modular. By precomputing the contributions of each drug across all regimens, we can transform the impact calculation into a straightforward matrix multiplication, simplifying aggregation across countries and drugs. This would not only improve computational efficiency but also make the system more scalable for larger datasets or multiple scenario analyses. 

