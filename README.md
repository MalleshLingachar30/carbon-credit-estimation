# Carbon Credit Estimation Module
### Open-Source CO₂ Sequestration Calculator for *Santalum album* (Indian Sandalwood) Agroforestry

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Standard: Verra VCS](https://img.shields.io/badge/Standard-Verra%20VCS-blue.svg)](https://verra.org/programs/verified-carbon-standard/)
[![Standard: Gold Standard](https://img.shields.io/badge/Standard-Gold%20Standard-yellow.svg)](https://www.goldstandard.org/)

---

## Overview

This open-source module calculates carbon dioxide (CO₂) sequestration for Indian Sandalwood (*Santalum album*) plantations across India. It provides transparent, auditable carbon credit estimation aligned with **Verra Verified Carbon Standard (VCS)** and **Gold Standard** methodologies.

Developed by **Grobet India Agrotech Pvt Ltd** (Bengaluru, Karnataka) as part of the [Sandalwood Intelligence Platform](https://sandalwood.growbetterindia.com), and open-sourced to enable smallholder farmers, agroforestry practitioners, and ESG researchers to access verified climate impact measurement.

---

## Why Sandalwood for Carbon Credits?

- *Santalum album* is a slow-growing, high-density hardwood with a 15–17 year harvest cycle
- Heartwood density and biomass accumulation make it one of the highest per-hectare carbon sequestration species in tropical agroforestry
- India holds 90%+ of the world's natural sandalwood; Karnataka alone has 2.5 lakh hectares suitable for cultivation
- Smallholder farmers growing sandalwood have never had access to verifiable carbon credit data — this module changes that

---

## Scientific Basis

The module applies:

- **Allometric equations** specific to *Santalum album* sourced from peer-reviewed research published by the **Institute of Wood Science and Technology (IWST), Bengaluru**
- **Biomass expansion factors (BEF)** for above-ground and below-ground biomass
- **Root-to-shoot ratios** validated for Indian tropical dry deciduous forest conditions
- **IPCC Tier 2 methodology** for biomass carbon stock estimation
- Carbon fraction of dry matter: **0.47** (IPCC default for hardwoods)

### Core Formula

```
CO₂ Sequestered (tonnes/ha/year) =
  ΔBiomass (tonnes/ha/year) × BEF × (1 + R) × CF × (44/12)

Where:
  ΔBiomass  = Annual above-ground biomass increment (tonnes/ha/year)
  BEF       = Biomass Expansion Factor (1.15 for Santalum album)
  R         = Root-to-shoot ratio (0.26 for tropical dry deciduous)
  CF        = Carbon fraction (0.47)
  44/12     = Molecular weight ratio of CO₂ to C
```

---

## Estimation Parameters by Growth Stage

| Year Range | Avg Height (m) | DBH (cm) | Biomass Increment (t/ha/yr) | CO₂ (t/ha/yr) |
|------------|---------------|----------|----------------------------|----------------|
| 1–3        | 0.5–1.5       | 1–3      | 0.8–1.2                    | 1.4–2.1        |
| 4–7        | 2.0–4.5       | 4–8      | 1.5–2.8                    | 2.6–4.9        |
| 8–12       | 5.0–8.0       | 9–15     | 2.5–4.0                    | 4.4–7.0        |
| 13–17      | 8.0–12.0      | 16–22    | 1.8–2.5                    | 3.2–4.4        |

*Values represent Karnataka/South India conditions. Adjust for regional climate variability.*

---

## Usage

### Input Parameters

```json
{
  "plantation_area_hectares": 1.0,
  "tree_density_per_hectare": 400,
  "plantation_age_years": 7,
  "soil_type": "red_laterite",
  "region": "karnataka_south",
  "host_plant_coverage_percent": 60
}
```

### Sample Output

```json
{
  "annual_co2_sequestered_tonnes": 3.84,
  "cumulative_co2_at_age_tonnes": 21.6,
  "carbon_credits_vcs_eligible": 21.6,
  "estimated_credit_value_usd": 324,
  "methodology": "IPCC Tier 2 / Verra VCS VM0047",
  "confidence_level": "medium",
  "notes": "Based on IWST allometric equations for Santalum album, Karnataka conditions"
}
```

---

## Alignment with Carbon Standards

| Standard | Applicable Methodology | Status |
|----------|----------------------|--------|
| Verra VCS | VM0047 Afforestation, Reforestation and Revegetation | ✅ Aligned |
| Gold Standard | Land Use & Forests Activity Requirements | ✅ Aligned |
| IPCC | Tier 2 Biomass Carbon Stock | ✅ Aligned |
| India BIS | IS 17534 Sandalwood Grading | ✅ Referenced |

---

## Limitations & Disclaimers

- Estimates are based on average growth data; actual sequestration varies with microclimate, soil health, host plant management, and irrigation
- **Spike disease** (*Candidatus* Phytoplasma santalum) can reduce biomass accumulation by 40–100%; affected trees should be excluded from credit calculations
- This module provides estimation for planning purposes; formal carbon credit issuance requires third-party verification by an accredited VVB (Validation/Verification Body)
- Not a substitute for field measurement in formal carbon project registration

---

## Contributing

Contributions welcome from agroforestry scientists, climate researchers, and carbon standard practitioners. Please open an issue or submit a pull request.

Areas needing contribution:
- Regional allometric equations for Andhra Pradesh, Tamil Nadu, Rajasthan conditions
- Integration with satellite biomass monitoring (Sentinel-2, BIOMASS mission)
- Spike disease impact correction factors

---

## Developed By

**Grobet India Agrotech Pvt Ltd**
Malleswaram, Bengaluru, Karnataka — 560003
CIN: U62090KA2023PTC170106

**Mallesh Lingachar** — CEO & Karnataka Forest Department Certified Sandalwood Trainer
**Dr. Chandrashekar Biradar** — Co-Director & Agroforestry Scientist

Platform: [sandalwood.growbetterindia.com](https://sandalwood.growbetterindia.com)
Contact: ml@feedbacknfc.com

---

## Licence

MIT Licence — free to use, modify, and distribute with attribution.
See [LICENSE](./LICENSE) for details.
