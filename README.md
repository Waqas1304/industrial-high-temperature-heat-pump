# Industrial high-temperature heat pumps vs gas boilers: what carbon price closes the gap?


A techno-economic model that compares an industrial high-temperature heat pump (IHTHP) with a natural gas steam boiler for 120–150 °C process heat. It links a thermodynamic cycle model (CoolProp) to a levelised cost of heat (LCOH) calculation, then asks how EU carbon prices and electricity/gas price ratios change the result.

## Research question

At current EU energy prices, what EU ETS carbon price makes a heat pump supplying 140 °C process heat cost-competitive with a gas boiler? Which lever moves that threshold the most: the carbon price, the electricity/gas price ratio, investment cost or operating hours?

## Method

1. **Cycle model.** Single-stage vapour-compression cycle with R1233zd(E), a low-GWP refrigerant used in commercial HTHPs [13]. Properties come from CoolProp [14]. Compressor isentropic efficiency is 0.70, with a 5 K pinch in each heat exchanger and 10 K suction superheat. The reference case is 60 °C waste heat lifted to 140 °C, which matches the worked example in the Danish Energy Agency catalogue.
2. **Validation.** The model COP at the reference case (2.03) is 15 % below the DEA reference value of 2.4. This is expected, since a single-stage cycle with conservative pinches performs worse than commercial multi-stage machines, so the results are conservative for the heat pump. Across all cases the model reaches 37–58 % of the Carnot COP.
3. **LCOH.** Investment is annualised with the capital recovery factor, then fixed O&M, variable O&M and energy costs are added. The gas boiler also pays the EU ETS price on its CO₂ emissions.
4. **Scenarios.** Three ETS prices (€74, €126 and €227/t) combined with three electricity/gas price ratios (2.0, 3.0 and 4.0).
5. **Break-even carbon price.** The ETS price at which LCOH(heat pump) = LCOH(boiler), solved analytically.
6. **Sensitivity.** One-at-a-time variation of CAPEX, full-load hours, discount rate, price ratio and compressor efficiency.

## Input data

| Parameter | Value | Source |
|---|---|---|
| HTHP investment | 1,750 €/kW_th (1.55 M€/MW + 0.20 M€/MW for lift > 75 K) | DEA (2026) [1, 2] |
| HTHP fixed / variable O&M | 0.09 %/yr of CAPEX / 4.09 €/MWh | DEA datasheet 302.b, via PyPSA technology-data [3] |
| HTHP lifetime | 20 years | DEA 302.b [3] |
| Gas steam boiler investment | 63.3 €/kW_th | DEA datasheet 311.1c [3] |
| Boiler fixed / variable O&M | 3.9 %/yr / 1.33 €/MWh | DEA 311.1c [3] |
| Boiler efficiency / lifetime | 92.5 % / 25 years | DEA 311.1c [3] |
| Discount rate | 4 % (real) | DEA catalogue [1] |
| Full-load hours | 5,000 h/yr | DEA heat pump vs boiler example [4] |
| Electricity price | 183.7 €/MWh | Eurostat nrg_pc_205, EU avg., H2 2025, 500–2,000 MWh band, excl. VAT [5] |
| Natural gas price | 60.5 €/MWh | Eurostat nrg_pc_203, EU avg., H2 2025, 10,000–100,000 GJ band, excl. VAT [6] |
| Gas emission factor | 0.202 tCO₂/MWh (56.1 t/TJ) | IPCC 2006 Guidelines [7] |
| ETS price, 2025 | €74/t | ESMA Carbon Markets Report 2026 [8] |
| ETS price, 2030 | €126/t | GMK Center analyst consensus [9] |
| ETS price, 2035 | €227/t (nominal) | LSEG Carbon Research forecast [10] |

## Results

| Indicator | Value |
|---|---|
| COP, 60 → 140 °C | 2.03 |
| LCOH heat pump | 120.7 €/MWh |
| LCOH gas boiler (ETS €74/t) | 84.2 €/MWh |
| Break-even ETS price | €241/tCO₂ |
| Electricity/gas ratio needed for parity at today's ETS price | 1.81 (EU average today: 3.04) |

Break-even carbon price by supply temperature (60 °C source, EU-average prices):

| Sink temperature | COP | Break-even ETS price |
|---|---|---|
| 120 °C | 2.96 | €110/t |
| 130 °C | 2.46 | €169/t |
| 140 °C | 2.03 | €241/t |
| 150 °C | 1.63 | €344/t |


## What the results suggest

At 2025 EU-average prices the heat pump is about 36 €/MWh more expensive than the gas boiler at 140 °C. Energy cost explains most of this. Electricity costs about three times as much as gas per MWh, and a COP of 2 is not enough to make up for it.

The electricity/gas price ratio has the largest effect on the result. Moving the ratio from 3.0 to 2.0 cuts the break-even carbon price from €241/t to €100/t. Raising CAPEX by 0.2 M€/MW, by contrast, moves it by only about €14/t. So policies that reduce levies and network charges on industrial electricity may do more for heat pump uptake than a higher ETS price alone.

Supply temperature also matters a lot. At 120 °C the break-even price (€110/t) is close to forecast 2030 ETS prices. At 150 °C it is more than four times today's price.

There is also a regulatory coverage gap. EU ETS1 only covers combustion installations above 20 MW total rated thermal input (Directive 2003/87/EC, Annex I) [11]. Many small and medium industrial boilers therefore face no carbon price at all, so the break-even values above are out of reach for them under current rules. ETS2, which will put a price on fuels for these users, has been postponed to 2028 [12].

## Limitations

- Single-stage cycle with constant isentropic efficiency, one refrigerant and no part-load behaviour.
- Annual-average EU prices: no hourly prices, no value from flexibility or thermal storage, and no country-level differences.
- HTHP investment cost is held constant across sink temperatures.
- No grid connection costs, subsidies, free ETS allocation or indirect carbon costs in the electricity price.

## Possible extensions

Multi-stage and cascade cycles, country-specific tariff and levy structures, hourly price profiles with storage, sector-specific temperature profiles, and the cost of regulatory compliance included in the LCOH.


## References

1. Danish Energy Agency (2026). *Technology Data for Industrial Process Heat*, catalogue updated April 2026, datasheets January 2026. https://ens.dk/en/analyses-and-statistics/technology-data-industrial-process-heat
2. Danish Energy Agency (2026). *Technology Brief: Revisions of chapters on process heating in the Technology Catalogue*. https://ens.dk/media/7778/download
3. PyPSA technology-data, `outputs/costs_2025.csv` (values derived from DEA *Technology Data for Industrial Process Heat*). https://github.com/PyPSA/technology-data
4. Energinet / Danish Energy Agency (2020). *New Catalogue on Industrial Process Heating*. https://en.energinet.dk/analysis-and-research/news-about-the-technology-catalogues/news-on-the-technology-catalogues-2
5. Eurostat (2026). Electricity prices for non-household consumers, dataset nrg_pc_205.
6. Eurostat (2026). Gas prices for non-household consumers, dataset nrg_pc_203.
7. IPCC (2006). *2006 IPCC Guidelines for National Greenhouse Gas Inventories*, Vol. 2, Ch. 2, Table 2.2.
8. ESMA (2026). *EU Carbon Markets Report 2026*. https://www.esma.europa.eu/sites/default/files/2026-07/ESMA50-481369926-34622_Carbon_markets_report_2026.pdf
9. GMK Center (2025). EU carbon price consensus forecast. https://gmk.center/?p=116899
10. LSEG Carbon Research (2025). *EU ETS Long-Term Supply, Demand & Price Forecast*. https://www.lseg.com/content/dam/data-analytics/en_us/documents/reports/lseg-eu-ets-supply-demand-and-pricing-forecast-summary.pdf
11. Directive 2003/87/EC establishing a scheme for greenhouse gas emission allowance trading, Annex I (as amended).
12. ICAP (2026). EU officially adopts the 2040 climate target, postpones ETS 2 by one year. https://icapcarbonaction.com/en/news/eu-reaches-agreement-2040-climate-target-postpones-ets-2-one-year
13. Arpagaus, C., Bless, F., Uhlmann, M., Schiffmann, J., Bertsch, S.S. (2018). High temperature heat pumps: Market overview, state of the art, research status, refrigerants, and application potentials. *Energy* 152, 985–1010.
14. Bell, I.H., Wronski, J., Quoilin, S., Lemort, V. (2014). Pure and pseudo-pure fluid thermophysical property evaluation and the open-source thermophysical property library CoolProp. *Industrial & Engineering Chemistry Research* 53(6), 2498–2508.

## Author

Muhammad Waqas Saleem (Erasmus Mundus ME3+). [LinkedIn](https://www.linkedin.com/in/muhammadwaqassaleem1304/) · [GitHub](https://github.com/waqassaleem1304)
