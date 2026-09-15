# ISDA SIMM Initial Margin Calculator

An Excel-based implementation of the ISDA Standard Initial Margin Model (SIMM), 
built around a 24-trade case study spanning all major asset classes.

## Case study scope
24 trades covering:
- Equity (index forwards, options, futures, total return swap)
- FX (forwards, options, swaps)
- Commodity (energy, precious/base metals — forwards, futures, options, swaps)
- Interest Rate (swaps, OIS, swaptions, caps, FRAs)
- Credit (single-name CDS, CDS index, index options, spread forwards)

## Status
- ✅ **Equity risk class — complete**: trade classification into SIMM risk class/bucket, 
  Black-Scholes delta/vega/curvature sensitivity calculations, concentration threshold, 
  ratio and multiplier adjustments, weighted sensitivity aggregation
- 🔲 **FX, Commodity, Rate, Credit risk classes** — in progress
- 🔲 **Correlation aggregation and final IM computation** (cross-bucket/cross-risk-class 
  aggregation per SIMM methodology)
- 🔲 **VBA automation** — planned, to replace manual sheet-by-sheet trade classification 
  and sensitivity calc with macros
- 🔲 **Python build** — planned, for a more scalable/auditable version (likely pandas + 
  numpy for sensitivities, possibly QuantLib for curve construction)

## Methodology (equity risk class, as built)
- Market data: risk-free curves, dividend yields, implied vols per trade
- Black-Scholes option pricing → delta, vega, gamma
- Curvature via up/down shock scenarios (+15%/-15%) on spot, per SIMM shock convention
- Concentration risk: bucket-level concentration threshold, ratio, and multiplier applied 
  to delta/vega/curvature sensitivities
- Interest rate delta component captured separately for equity-linked swaps (e.g. total 
  return swap financing leg)

## Tools
Excel (current) → VBA (next) → Python (planned)

## Notes
All trade data and market rates are illustrative/hypothetical — built for methodology 
demonstration, not derived from real counterparty positions.
