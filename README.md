# Compound Interest Calculator

A single-page web app that works out how much a starting balance plus regular yearly additions will grow to, and charts that growth year by year and adds a growth chart, a breakdown of the total, and a year-by-year schedule.

**Live page:** https://mpioszak.github.io/compoundcalc/

## Features

- **Future value** of your investment, updated as you type
- **Breakdown** of the final balance into starting principal, total additions and interest earned, each with its share of the total
- **Growth chart**: a stacked bar for each year showing principal, additions and interest; hover a bar for exact amounts and that year's balance
- **Year-by-year schedule**: a collapsible table of the amount added, interest earned, running totals and balance for every year
- Light and dark themes that follow your system setting
- Works on phones and desktops

## Inputs

| Input | Description |
|---|---|
| Current principal | The amount you start with today |
| Annual addition | How much you add each year, split evenly across the compounding periods |
| Years to grow | 1 to 100 years |
| Annual interest rate | The yearly rate, as a percentage |
| Compounded | Annually, semiannually, quarterly, monthly, weekly or daily |
| Make additions at | The start or end of each compounding period |

## How it calculates

The calculator steps through every compounding period instead of using a closed-form formula, so the yearly figures in the chart and table come straight from the same loop as the total.

With annual rate `r`, `n` compounding periods per year and annual addition `A`, each period:

1. If additions are at the **start** of the period, add `A / n` to the balance.
2. Add interest: `balance × r / n`.
3. If additions are at the **end** of the period, add `A / n` to the balance.

This gives the same result as the standard formulas:

```
End of period:   FV = P(1 + r/n)^(nt) + (A/n) × [((1 + r/n)^(nt) − 1) / (r/n)]
Start of period: FV = P(1 + r/n)^(nt) + (A/n) × [((1 + r/n)^(nt) − 1) / (r/n)] × (1 + r/n)
```

### Check against moneychimp

For $1,000 principal, $100 annual addition, 5 years, 5% compounded annually:

| Additions at | Result |
|---|---|
| End of period | $1,828.84 (matches moneychimp) |
| Start of period | $1,856.47 |

## Running it locally

The whole app is one file, [compound-interest.html](compound-interest.html), with no build step. Open it in any modern browser. It needs an internet connection to load the chart library and fonts.

## Built with

- Plain HTML, CSS and JavaScript
- [Chart.js 4.4.1](https://www.chartjs.org/), loaded from cdnjs
- Google Fonts: Bricolage Grotesque, Public Sans and JetBrains Mono

## Notes

- Results are estimates. They assume a fixed interest rate and do not account for taxes, fees or inflation.
- This is not financial advice.
