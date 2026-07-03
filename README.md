# Digital Herbarium Label Data Parser

## Project Background
As an M.Sc. graduate in plant sciences, I developed this Python-based data cleaning pipeline to bridge the gap between traditional field botany collection logs and modern biodiversity database standards. 

## Botanical Data Tasks Solved:
1. **Nomenclature Corrections:** Automatically strips rogue whitespaces and enforces strict *Genus species* botanical capitalization rules (e.g., transforming `azadirachta INDICA` to `Azadirachta indica`).
2. **Temporal Unification:** Harmonizes varying field date notations into the international standard `YYYY-MM-DD` format.
3. **Institutional Meta-Tagging:** Appends institutional coding (`HERB-MSC-2026`) crucial for digitized museum/herbarium catalogs.

## Tech Stack
- **Language:** Python 3
- **Libraries:** Pandas (Data manipulation)
