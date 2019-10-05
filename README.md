# Financial Report

The financial report gathers Harold's personal finance data pulled from Plaid and the hiistorical security prices from IEX. We ran some data analysis to determine if the current portfolio will yield the customer's income requirements.

## Income Details

We got the following income data using PLAID's API method **Income**

| Prev Year's Gross Income | Current Monthly Income | Projected Yearly Income |
| --- | --- | --- |
| $7285 | $500 | $6085 |

## Budget Analysis

We also pulled account transactions for last 90 days from PLAID using API method **Transaction**. We analyzed the spending amount per category for the past 90 days.

| Category | Amount |
| ---- | --- |
| Food and Drink | $1105.73 |
| Payment | $2103.50 |
| Recreation | $78.50 |
| Shops | $500.00 |
| Transfer | $6845.78 |
| Travel | $11.73 |

![90 days spending](Resources/Images/spending_90days.png)

Overall amoount Harold spent around $10645.24 as shown below

![Expense_per_month](Resources/Images/Expenses_per_month.png)

## Retirement Planning

We used a portfolio consisting of stocks and bonds to build a retirement plan simulating historical data to project returns over time.

## Methodology

In running the simulation, we performed the following steps:

1. Take the historical closing prices of SPDR S&P 500 ETF (SPY) and iShares Core U.S. Aggregate Bond ETF (AGG) from the previous year.
2. Calculate average daily returns and volatility using standard deviation.
3. Assuming normal probability distribuition and taking into consideration average daily return and volatility, project portfolio cumulative returns from the last closing price and run 500 simulations over the 30 years (252 * 30 trading days), with portfolio weightage of 60% stocks ans 40% bonds.
4. Analyze results of simulations.

## Analysis

![Simulation](Resources/Images/monte_carlo_simulation_30_years.png)

We then calculated cumulative returns for the last row of the simulation and we found it falls in the range 0.5636 to 17.2581.

Narrowing it to a 90% confidence interval, the portfolio could yield 1.3827 to 8.7909.

![Confidence](Resources/Images/90_percent_confidence_interval.png)

Calculating the return at 10th, 50th, and 90th percentiles and an initial investment of $50,000, we get:

| Percentile | Ending Cumulative Return | Portfolio Return |
| --- | --- | --- |
| 10 | 1.8412 | $ 92,058.69 |
| 50 | 3.5159 | $ 175,798.48 |
| 90 | 7.0410 | $ 352,050.91 |

Now let's assume a 4% withdrawal rate at retirement, we find that the 10th percentile retirement income of $3,682.35 is less than the projected income of $6,085.00, suggesting not enough confidence to determine whether the portfolio return could meet the annual income requirement.

Later we increased 50% in the initial investment amount we foumd that portfolio yields a 10th percentile retirement income of $5,523.52 which still fell short of the projected income.

As an optional challenge we used the Monte Carlo data to calculate cumulative returns at 5%,50% and 95% quantiles. The following chart displays how the cumulative returns change over the life of the investment.

![option_challenge](Resources/Images/optional_challenge.png)
S