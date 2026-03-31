# Causal Inference for Digital Advertising

## Overview
This project evaluates whether observational methods can approximate experimental results when measuring the effectiveness of digital advertising.

Using a simulated Facebook ad campaign dataset with 2 million users, I compare:
- Experimental lift from a randomized controlled trial (RCT)
- Naive observational estimates
- Regression adjustment
- Inverse Probability Weighting (IPW)
- Double Machine Learning (Double ML)

The goal is to understand whether costly experiments can be replaced with observational approaches without sacrificing accuracy.

## Dataset
The dataset contains user-level information including:
- Demographics and engagement metrics
- Treatment assignment (Z)
- Ad exposure (W)
- Conversion outcome (Y)

The full dataset is not included due to size constraints.

Download it here:  
https://drive.google.com/uc?export=download&id=11XMEbxqF5X5_Hk2V82rT5cYz1PBz_qZn

After downloading, place the file in the same directory as the notebook:

AdVantage.csv

## Methodology
The analysis follows a progression from experimental ground truth to observational estimation:

1. Randomization check to validate experimental design  
2. Calculation of ATT and ITT from the RCT  
3. Naive comparison of exposed vs unexposed users  
4. Regression adjustment with increasing model complexity  
5. Inverse Probability Weighting (IPW)  
6. Double Machine Learning (Double ML)  

Each method is evaluated relative to the experimental benchmark.

## Results
- True ATT (RCT): approximately 5.6 percentage points  
- Naive estimate: significantly overstated due to selection bias  
- Regression adjustment: reduces bias but does not eliminate it  
- Double ML: closest observational estimate, but still inflated  

Observational methods consistently overestimate the impact of advertising.

## Business Implications
If all eligible users had been targeted, the campaign would have generated approximately 92,462 incremental conversions, compared to 46,301 under the RCT design.

However, using the Double ML estimate would have projected 197,780 incremental conversions, overstating the true impact by more than 100,000 conversions when scaled to the full population.

This highlights a tradeoff between short term performance and measurement quality. Running an experiment sacrifices some conversions in the short term but provides a reliable estimate of causal lift. Targeting all users maximizes immediate conversions but risks overstating effectiveness and distorting future decisions.

In practice, the value of experimentation depends on how heavily measurement informs future budget allocation and how costly misestimation would be at scale.

## Technologies
- Python  
- pandas  
- statsmodels  
- scikit-learn  
- DoubleML  

## Takeaway
Observational methods can approximate experimental results, but even advanced approaches like Double ML can meaningfully overstate impact.

Accurate measurement is critical when results are used to guide future decisions.
