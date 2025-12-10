Objective:
Build a real-time performance attribution dashboard using the Brinson-Fachler model.
Fetch live financial data (sector ETFs) to compute and visualize attribution components.

Process
Data Collection:
Sector ETF prices (XLK, XLF, XLV, XLE) downloaded using yfinance.
Daily returns computed and aggregated into cumulative period returns.

Portfolio Setup:
Custom Portfolio Weights and Benchmark Weights.
Weights normalized to ensure consistency.

Brinson Attribution Calculation:
Allocation Effect:(Portfolio Weight – Benchmark Weight) × Benchmark Return
Selection Effect:Benchmark Weight × (Portfolio Return – Benchmark Return)
Interaction Effect:(Portfolio Weight – Benchmark Weight) × (Portfolio Return – Benchmark Return)

Total Attribution computed as the sum of all effects.

Dashboard Visualization
Two-panel matplotlib dashboard:
Panel 1: Allocation, Selection, Interaction
Panel 2: Total Attribution

Results (Using Real ETF Numbers)
Brinson Attribution Results Table

| Sector  | Portfolio Weight | Benchmark Weight | Portfolio Return | Benchmark Return | Allocation    | Selection | Interaction | **Total Attribution** |
| ------- | ---------------- | ---------------- | ---------------- | ---------------- | ------------- | --------- | ----------- | --------------------- |
| **XLE** | 0.15             | 0.15             | 0.670145         | 0.670145         | 0.000000      | 0.000000  | 0.000000    | **0.000000**          |
| **XLF** | 0.20             | 0.30             | 0.314028         | 0.314028         | **-0.031403** | 0.000000  | -0.000000   | **-0.031403**         |
| **XLK** | 0.40             | 0.35             | 1.141924         | 1.141924         | **+0.057096** | 0.000000  | 0.000000    | **+0.057096**         |
| **XLV** | 0.25             | 0.20             | 0.423389         | 0.423389         | **+0.021169** | 0.000000  | 0.000000    | **+0.021169**         |


Interpretation

Allocation Effect:
Technology (XLK) added +5.71%, showing that overweighting the strongest-returning sector significantly boosted performance.
Healthcare (XLV) contributed +2.12%, also due to a beneficial overweight.
Energy (XLE) contributed 0%, since portfolio and benchmark weights matched.
Financials (XLF) detracted −3.14% because the portfolio underweighted a sector that delivered positive returns.

Selection Effect:
Selection effect is 0 across all sectors — portfolio and benchmark ETF returns were identical.
This indicates no stock-picking or selection alpha, only allocation decisions drove results.

Interaction Effect:
Interaction effect is near zero for all sectors, confirming no compounding effect from combined allocation + selection differences.

Total Active Return Attribution:
The portfolio’s strongest contributor was XLK with +5.71%, driven entirely by overweighting.
XLV added +2.12%, also a result of beneficial allocation.
XLF reduced total returns by −3.14%, making it the only detractor.
XLE was neutral, contributing 0%.

Key Takeaway:
The portfolio’s outperformance was driven entirely by smart sector allocation decisions, not selection.
Overweighting Technology (XLK) and Healthcare (XLV) added a combined +7.83%, far outweighing the −3.14% drag from underweighting Financials (XLF).
Energy (XLE) remained neutral.
Overall, the portfolio generated positive active return purely due to effective sector tilting, showing that allocation choices—not security selection—were the key drivers of performance.

Tech Stack:Numpy,Pandas,Yfinance,Matplotlib.

Future Enhancements:
Add multi-period (geometric) attribution
Add Plotly for interactive charts
Allow custom tickers and full-equity universes
Enable PDF/PNG export of attribution report
Add cumulative active return attribution
Integrate factor attribution (Fama–French, Barra-like)
Support fixed income + equity attribution
