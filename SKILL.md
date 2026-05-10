---
name: noresm
description: >
  Progressive-disclosure skill for the Norwegian Earth System Model (NorESM),
  a CESM-derived coupled climate / Earth-system model with NorESM-specific
  ocean (BLOM/MICOM-derived), aerosol (OsloAero), and biogeochemistry
  (HAMOCC, iHAMOCC). Covers the NorESM superproject, manage_externals
  bootstrap, the CESM-derived case workflow, NorESM-specific compsets,
  and the link to NorESM-1 / NorESM-2 documentation.
version: 0.1.0-scaffold
tags:
  - earth-science
  - climate-model
  - earth-system-model
  - noresm
  - blom
  - hamocc
  - oslo-aero
  - cesm-derived
  - norway
  - fortran
---

# NorESM (Norwegian Earth System Model) Guide

> **NorESM** = Norwegian Earth System Model, a CESM-derived coupled Earth-system model.
> Maintainer: NorESM Climate Modeling Consortium (Norwegian institutions)
> Source: https://github.com/NorESMhub/NorESM
> Docs: https://noresm-docs.readthedocs.io
> Website: https://www.noresm.org
> Skill author: Koutian Wu (ktwu01@gmail.com)
> Skill version: 0.1.0-scaffold

**What NorESM does:** Provides a coupled atmosphere–ocean–land–sea-ice climate model with Norwegian-developed components for ocean dynamics (BLOM, derived from MICOM, an isopycnal-coordinate ocean), ocean biogeochemistry (HAMOCC / iHAMOCC), and aerosols (OsloAero). The host framework is CESM-derived: CIME-based case control, **MCT coupler** (CMEPS is a CESM2.2+/CESM3 thing, not yet the NorESM2 production standard), **CLM5** as the land component (a specific tag of CTSM, so look for `user_nl_clm` not `user_nl_ctsm`), CAM atmosphere, CICE sea-ice. Used by Norwegian climate research and contributes to CMIP.

**Who this skill is for:** Researchers running CMIP-class climate experiments with NorESM, developers porting NorESM to a new machine, and anyone needing to understand which parts are NorESM-specific vs inherited from CESM.

---

## Quick Decision Tree

```
"What do I need?"
│
├─ 🆕 What is NorESM, what is CESM-derived, what is NorESM-specific?
│  └─ Read: reference/overview.md
│
├─ 📥 Bootstrap the model (manage_externals, Externals.cfg)
│  └─ Read: reference/bootstrap.md
│
├─ 🚀 Run a case (CIME workflow, NorESM compsets)
│  └─ Read: reference/running-a-case.md  (also see cesm-skill)
│
├─ 🌊 BLOM ocean (isopycnal, MICOM-derived)
│  └─ Read: reference/blom-ocean.md
│
├─ 🧪 HAMOCC / iHAMOCC ocean biogeochemistry
│  └─ Read: reference/hamocc-bgc.md
│
├─ ☁️ OsloAero aerosol scheme
│  └─ Read: reference/osloaero.md
│
└─ 🐛 NorESM-specific build/run issues
   └─ Read: reference/debugging.md
```

---

## Repo Layout (verified from clone)

```
NorESM/
├── cime_config/                          # NorESM-specific CIME configuration
├── manage_externals/                     # External-component fetcher
├── Externals.cfg                         # Components for stable releases
├── Externals_continuous_development.cfg  # Components for development tip
├── img/                                  # Logo etc.
├── README.md
├── LICENSE.txt
├── LICENSE-CESM.txt
├── Copyright-CESM.txt
└── CONTRIBUTING.md
```

This is a **thin meta-repo**. The actual model code (CAM, CLM/CTSM, BLOM, CICE, HAMOCC, OsloAero) is fetched into a `components/` tree by `manage_externals/checkout_externals` based on `Externals.cfg`.

---

## Critical Rules

1. **The repo is intentionally tiny.** Don't be confused by the small footprint, you must run the externals tool to populate `components/`.
2. **Two externals files.** `Externals.cfg` (stable / release) vs `Externals_continuous_development.cfg` (CD tip). Pick deliberately.
3. **NorESM uses CIME.** The case workflow (`create_newcase`, `case.setup`, `case.build`, `case.submit`) is the same as CESM; differences are in compsets and component versions.
4. **Compsets:** standard NorESM2 compsets are `N`-prefixed (e.g., `NHIST`, `N1850`) where `N` denotes NorESM-specific component combinations.
5. **NorESM has its own license** layered on top of the CESM-derived parts. Read `LICENSE.txt`, `LICENSE-CESM.txt`, and `Copyright-CESM.txt`.

---

## Reference Index

| File | Topic |
|---|---|
| reference/overview.md | What is NorESM-specific |
| reference/bootstrap.md | manage_externals, Externals.cfg |
| reference/running-a-case.md | CIME workflow, NorESM compsets |
| reference/blom-ocean.md | Isopycnal ocean (BLOM/MICOM) |
| reference/hamocc-bgc.md | Ocean biogeochemistry |
| reference/osloaero.md | Aerosol scheme |
| reference/debugging.md | NorESM-specific issues |

## Critical agent gotchas (Gemini-reviewed)

- **NorESM grids are not CESM grids.** BLOM uses ocean-grid aliases like `tn14`, `tn21`. The CESM-equivalent grid string `f19_g17` becomes something like `f19_tn14` for NorESM. Verify in the NorESM compset XML before reusing CESM grid strings.
- **Compset names need a resolution tier.** Bare `N1850` is incomplete in production use; standard NorESM2 uses resolution-tagged compsets (look at the released compset list for the `_LM`, `_MM`, `_HH` etc. variants).
- **`Externals.cfg` (or release-named variant) is the production manifest.** `Externals_continuous_development.cfg` may pull unstable component versions; only use it deliberately.
- **Input data is hosted on Norwegian infrastructure** (NIRD/Sigma2), not the standard NCAR mirrors. `check_input_data` may fail without configured server paths for NorESM-specific files (aerosol forcing, ocean initial conditions, etc.).
- **`user_nl_clm` is the file** for land-side namelist customization (since the land tag is CLM5).

## Status

Scaffold (v0.1.0-scaffold). Layout verified against the cloned NorESM superproject, with Gemini critique pass on 2026-05-09 to correct coupler (MCT not CMEPS), land-component naming (CLM5 not CTSM), and add NorESM-specific grid/data caveats. Operational depth being filled in.
