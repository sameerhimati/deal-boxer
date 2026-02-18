# deal-boxer

Filters commercial properties against investment criteria ("deal boxes"). Tags each property with which investment strategy it fits: small bay industrial, sale-leaseback, operating business, or none.

## What it replaces
Analysts manually screening properties against investment criteria spreadsheets.

## Usage
```bash
deal-boxer filter --input properties.csv --output tagged.csv
deal-boxer filter --input properties.csv --strategy small_bay_industrial
deal-boxer check --address "123 Main St, Dallas, TX"
```

## Deal Box Strategies
- **small_bay_industrial** — 10K-50K SF industrial, multi-tenant potential, value-add
- **sale_leaseback** — owner-occupied, strong credit tenant, long-term lease
- **operating_business** — business + real estate, owner retiring or distressed

## Input / Output

**Input:**
- CSV or JSON with property records (must include: `sqft`, `property_type`, `city`, `state`, `zoning`, `vacancy_pct`, `entity_type`)
- Optional: `--strategy` flag to filter for a specific deal box
- Optional: custom criteria config (YAML)

**Output:**
- CSV or JSON with original columns + `deal_box` column (one of: `small_bay_industrial`, `sale_leaseback`, `operating_business`, `none`)
- Properties can match multiple deal boxes (comma-separated)
- Exit code 0 on success, 1 on failure
- stdout: filter summary (count per deal box, total matches, total excluded)

## Stack
- Python 3.14, Pydantic
- Typer + Rich for CLI

## Status
🟢 Core logic exists (porting from atlas monolith)
