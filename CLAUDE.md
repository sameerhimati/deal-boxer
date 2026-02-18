# deal-boxer

## What This Is
Investment criteria filter for CRE properties. Determines which deal box strategy (if any) a property fits.

## Key Constraints
- Deal box criteria are defined in config (YAML/JSON), not hardcoded
- A property can match multiple deal boxes
- Input: CSV/JSON of property data. Output: same data with deal_box column(s) added.
- Criteria include: SF range, property type, location, zoning, occupancy, owner type

## Architecture
- Strategy definitions: each deal box is a set of filter rules
- Filter engine: evaluates property against all strategies, returns matches
- CLI: batch filter or single-property check

## Tech
- Python 3.14, Pydantic, Typer + Rich
- No database — reads/writes files
- Use venv/bin/python and venv/bin/pytest
