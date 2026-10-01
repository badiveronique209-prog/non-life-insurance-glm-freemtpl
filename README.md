# Non-Life Insurance Pricing with GLM

I wanted to understand how car insurers set their prices, so I worked on French motor insurance data.

This notebook looks at claim frequency using the freMTPL2freq dataset. I used a Poisson GLM, which is the classic model for this kind of problem in insurance. I also made sure to handle exposure properly with an offset, because not all policies were observed for a full year.

Some things I noticed in the data:
- Young drivers (18-25) have about twice as many claims as older drivers
- Most policies are at Bonus-Malus 50, which is the best bonus level
- Exposure is quite spread out, so using log(Exposure) as offset was important

The model itself is simple but interpretable. I centered Bonus-Malus at 50, used One-Hot for categorical variables, and checked for overdispersion. On the test set I get RMSE around 0.237 and Gini around 0.25, which is reasonable for this dataset.

Next I would like to add a severity model and combine frequency and severity to get the pure premium. I also want to try a Negative Binomial model to see if it handles overdispersion better.

Tools: Python, pandas, statsmodels, sklearn

Dataset: download freMTPL2freq.csv from https://www.openml.org/d/41214 and put it in data/raw/