# InnoThon 2026: India 2047 Electricity Generation Forecast

Built for the ExxonMobil InnoThon 2026 challenge (pre-final round). This is an independent participant project, not affiliated with or endorsed by ExxonMobil.

A forecast of India's electricity **generation** in 2047, nationally and across the five NPP grid regions, with a source mix and a sensitivity analysis. Installed capacity and consumption are not used anywhere in the forecast or comparisons.

## Results

| | 2047 (TWh) | Range (TWh) |
|---|---|---|
| **India** | **3,779** | 3,064 to 4,494 |
| Western | 1,304 | 1,057 to 1,550 |
| Northern | 979 | 794 to 1,164 |
| Southern | 766 | 621 to 911 |
| Eastern | 666 | 540 to 792 |
| North Eastern | 64 | 52 to 76 |

National source mix, FY2024 to 2047: thermal 78.1% to 61.5%, hydro 7.9% to 5.3%, nuclear 2.8% to 2.2%, renewables 11.2% to 31.0%.

The range is the backtest error widened with the forecast horizon. It is not a statistical interval.

## Method

1. **National total.** Damped compound growth (damping 0.97, 10-year window), chosen over log-linear and Holt-damped trends by a rolling backtest on FY2007 to FY2024 generation (error 6.8% against 8.0% and 7.7%).
2. **Source mix.** Additive log-ratio of each source against thermal, with a damped trend (0.95).
3. **Regions.** Each region's 2047 share blends today's share of state generation with its forecast share of population and GSDP. The blend weight (0.95) was fitted by a backtest. A pure population and GDP driver model was tested and rejected (9.1% error against 6.8%).
4. **Sensitivity.** The 2047 total moves from 2,546 TWh at damping 0.90 to 5,217 TWh at 1.00, while the backtest error barely changes. The damping setting is therefore the main uncertainty.

## Limits

- State-wise generation on the NPP dashboard is conventional only, for a single year-to-date period. There is no yearly regional history and no regional split by source, so the source mix is national.
- Geography, climate, land availability and urbanization are not in the data used, so they are not modelled.
- The regional weight is fitted on one transition, so it is weakly determined. The notebook shows the drivers-only and no-change cases as bounds.
- Some national thermal values were read from a chart on the NPP dashboard (about 25 GWh precision).

## Repository

- `India2047_forecast.ipynb`: the full analysis. Run it top to bottom in Colab.
- `results/`: national history, national forecast and regional 2047 results.
- `data/regional_snapshot_conventional_ytd.csv`: state totals aggregated to regions.
- `slides/`: the mid-point review slides.

## Run it yourself

1. Open the notebook in Google Colab.
2. Download `renewable_energy_dataset.csv` (link below) and upload it to Colab for Cell 1.
3. Run all cells.

## Data sources

- Population and GSDP: `renewable_energy_dataset.csv` from https://github.com/chrisjaimyantony/renewable-india-dataset (not included here).
- Generation: the National Power Portal dashboard, https://npp.gov.in
**Live dashboard:** https://powerpath-2047-india-electricity-generation-forec.ai.studio
## Author

Shwetha Shaji, Dayananda Sagar College of Engineering.
