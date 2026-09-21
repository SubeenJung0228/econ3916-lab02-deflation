# The Data Portfolio — Deflating Economic Data: Nominal vs. Real

## Objective
This project applies price-index deflation to fifty years of U.S. wage data
and two decades of Big Mac prices to isolate genuine purchasing-power change
from currency devaluation, and builds a reusable deflation function for use
across future analyses.

## Methodology
- Pulled two FRED time series -- the Consumer Price Index (CPIAUCSL,
  1947-present) and Average Hourly Earnings (AHETPI, 1964-present) --
  directly from FRED's public CSV endpoint, requiring no API credential
- Built a reusable deflate_series() function implementing the standard
  deflation identity, Real = (Nominal / CPI) x Base-Year CPI, to rescale any
  nominal series into constant-dollar terms for a chosen base year
- Applied the function to average hourly earnings to construct a fifty-year
  nominal-vs-real wage comparison, and separately to The Economist's Big Mac
  Index panel to decompose U.S. burger price changes (2000-2026) into
  inflation and non-inflation components
- Verified the deflation output against three checks: that real and nominal
  values converge in the base year, that the base-year CPI reflects an
  annual average rather than a single month, and that the growth identity
  (1 + nominal) = (1 + real) x (1 + CPI) holds
- Extended the analysis with an interactive ipywidgets explorer allowing
  dynamic base-year selection and nominal/real toggling across both series

## Key Findings
- Nominal hourly earnings rose from $2.50 to $32.53 (1964-2026), an increase
  exceeding 1,200% -- but in constant 2020 dollars, real earnings moved only
  from $20.92 to $25.20, a real gain of roughly 20% over sixty-two years
- Real wages peaked in the early 1970s and did not durably regain that level
  for nearly five decades, pointing to a structural break rather than a
  simple slowdown in growth
- The U.S. Big Mac's nominal price rose 178% (2000-2026), but the real price
  rose only 43% while CPI rose 95% over the same window, confirming that
  roughly three-quarters of the sticker-price increase reflects broad
  inflation rather than a burger-specific cost increase
"""
