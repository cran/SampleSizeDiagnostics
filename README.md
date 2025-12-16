# Calculation of Sample Size for Diagnostic Studies

(Based on the Paper by Buderer - Pubmed ID 8870764)

## Overview

This repository provides tools for calculating the sample size required for diagnostic studies, based on the methodology described in the paper by Buderer. The paper incorporates the prevalence of disease into the sample size calculation for sensitivity and specificity.

### Link to Paper

[Statistical Methodology: I. Incorporating the Prevalence of Disease into the Sample Size Calculation for Sensitivity and Specificity](https://onlinelibrary.wiley.com/doi/epdf/10.1111/j.1553-2712.1996.tb03538.x)

## Installation

To use the `SampleSizeDiagnostics` package, you can install it from GitHub using the `devtools` package:

```r
library(devtools)
install_github("statpharm/SampleSizeDiagnostics")
library(SampleSizeDiagnostics)
```
## Usage

To understand how to use the package and its functions, you can access the help documentation:

```r
?SampleSizeDiagnostics 
```
## Example

Here is an example of how to calculate the sample size with given parameters:
This function call will calculate the required sample size for a diagnostic study with:

    Sensitivity (sn) of 0.9
    Specificity (sp) of 0.85
    Prevalence (p) of 0.2
    Half-width of the confidence interval (w) of 0.1 [margin of error; total CI width = 0.2]
    Confidence level (CI) of 0.95

```r
SampleSizeDiagnostics(sn = 0.9,
                      sp = 0.85,
                      p = 0.2,
                      w = 0.1,
                      CI = 0.95)
```
## Important Note About the Width Parameter
   
   ⚠️ **Critical:** The `w` parameter represents the **half-width** (margin of error) of the 
   confidence interval, not the total width.
   
   **What this means:**
   - `w = 0.1` creates a CI spanning **0.2 units** (estimate ±0.1)
   - If you want a total CI width of 0.1, use `w = 0.05`
   
   **Example:**
```r
   SampleSizeDiagnostics(sn = 0.9, sp = 0.85, p = 0.2, w = 0.1, CI = 0.95)
   # With w = 0.1 and sensitivity estimate of 0.9:
   # CI will be [0.80, 1.00] 
   # Half-width (margin of error) = 0.1
   # Total CI width = 0.20
```
   
   This follows the methodology in Buderer (1996).
