# ASML DCF Valuation Model

## Context
Learning project — building financial modelling literacy from real, fully public
data before eventually working up to a more complex blended-finance model. This
follows on from an earlier Excel-based learning track using Datadog (income
statement, VC-lens operating metrics, driver-based forecast). This project moves
to a code-based (Python/Jupyter) reusable DCF valuation engine, applied first to
ASML Holding N.V. (AEX/Nasdaq: ASML).

Build everything step by step, explaining each concept before or as it's added.
Don't skip ahead — confirm understanding before moving to the next module.

## Company
ASML Holding N.V. — reports in EUR under IFRS. Files annual reports plus SEC
20-F/6-K filings (dual Nasdaq listing). Discloses bookings/order backlog
quarterly (useful forward-looking revenue signal — EUV tools have long lead
times). Reports China revenue as a distinct disclosed line (relevant given
export-control exposure).

## Data sourcing rules (non-negotiable)
- Every hardcoded number must come from a real, cited source (ASML annual
  report, SEC filing, or quarterly press release) — no invented or "plausible"
  figures.
- Every hardcoded input gets a comment/docstring citing exactly where it came
  from (document name, page/section, date).
- If a needed input isn't publicly disclosed, flag it explicitly as an
  assumption rather than presenting it as sourced fact.
- Reporting currency: EUR (ASML's native reporting currency). Note any FX
  conversion explicitly if USD is ever needed.

## Model structure
- Reusable DCF engine (functions/classes taking an assumptions dict), not a
  one-off script — this should work for other companies later.
- 5-year explicit forecast horizon before terminal value.
- Terminal value: build BOTH Gordon Growth (perpetuity) and Exit Multiple
  methods, cross-checked against each other.
- WACC built up from CAPM (cost of equity) plus cost of debt and capital
  weights.
- Full bridge: revenue forecast -> unlevered FCF -> discounted to PV ->
  Enterprise Value -> equity value -> per-share value, compared to actual
  market price.

## Format
- Jupyter notebook, one section/concept per set of cells, markdown cells
  explaining each concept before the code that implements it.
- After running each cell/section, interpret the output in plain language
  (what the number means, what's driving it) before moving on.

## Testing
- Run the notebook end-to-end after every change; zero errors before
  considering a module "done."
