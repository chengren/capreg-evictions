# Capital Region Eviction Map

Interactive map of residential eviction filings by ZIP code in New York's Capital Region: Albany, Rensselaer, Saratoga and Schenectady counties.

**Live site:** https://chengren.github.io/capreg-evictions/

Companion statewide map (NYC vs. outside NYC): https://chengren.github.io/nys-eviction/

## What it shows

- Eviction filings by ZIP code, as a count or as annual filings per 1,000 renter households
- Any date range from September 2021 to the latest month in the data
- For each ZIP code: monthly filings, case outcomes (judgment of possession, warrants, legal representation) and a renter profile (rent, income, rent burden, poverty, unemployment, race and ethnicity of renter householders)

## Data

**Eviction filings.** NY State Unified Court System, deidentified landlord-tenant extract for city and district courts. This map uses the eight city courts in the four counties: Albany, Cohoes, Watervliet, Troy, Rensselaer, Schenectady, Mechanicville and Saratoga Springs. Commercial cases are excluded. Only aggregated ZIP-by-month counts are published here; no case-level records.

**Renter profile.** American Community Survey 2020-2024 5-year estimates for ZIP Code Tabulation Areas, via the Census API.

## Coverage

Town and village courts are not in the court extract. ZIP codes served mainly by those courts are shown as "no data", which does not mean there were no evictions. A ZIP code counts as covered when the city courts recorded at least 100 residential filings there. ZIP codes that straddle a city line are partly undercounted.

## Methods

- **Rate:** filings in the selected window ÷ months × 12 ÷ renter households × 1,000
- **Tiers:** quartiles of the January 2022 to latest-month rate across covered ZIP codes, fixed so a color means the same rate in every window
- **Income needed to afford rent:** median gross rent × 12 ÷ 0.30
- **Rent burden:** share of renter households paying 30% or more (cost-burdened) or 50% or more (severely burdened) of income on gross rent, among households for which the ratio is computed
- Months before January 2022 fall under New York's eviction moratorium and are partial.

## Files

```
index.html                    the page (D3.js, no build step)
data/eviction_zip_month.json  filings and outcomes by ZIP code and month
data/acs_zcta.csv             ACS renter profile by ZCTA
data/zcta_geo.geojson         ZCTA boundaries (2020)
data/county_geo.geojson       county boundaries (2020)
```

## Run locally

The page loads files from `data/`, so open it through a local server rather than double-clicking:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Contact

Maintained by [@chengren](https://github.com/chengren), School of Social Welfare, University at Albany, SUNY.
