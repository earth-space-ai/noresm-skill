# NorESM Skill

Progressive-disclosure skill for the [Norwegian Earth System Model](https://github.com/NorESMhub/NorESM) (NorESM), a CESM-derived coupled Earth-system model with NorESM-specific ocean (BLOM/MICOM), biogeochemistry (HAMOCC/iHAMOCC), and aerosols (OsloAero).

> **Skill author:** Koutian Wu (ktwu01@gmail.com)
> **Skill version:** 0.1.0-scaffold

> ⚠️ **Disclaimer — please read before using this skill.**
> This skill is **not a gold-standard reference**. It is a helper that lowers
> the barrier for new users to **get their hands dirty** with the model. AI
> agents (and the humans drafting this material) make mistakes; commands, file
> paths, namelist options, and physics explanations here can be wrong,
> incomplete, or out of date. **Always cross-check with the official model
> documentation, the source code, and a human expert before trusting any
> output for research, publication, or operational use.**

## What This Is

A guide to NorESM as a CESM-derived superproject: the `manage_externals` bootstrap, `Externals.cfg` choices, NorESM-specific compsets, and the science components that distinguish NorESM from upstream CESM (BLOM ocean, HAMOCC BGC, OsloAero).

## Status

Scaffold. Layout verified against the cloned `NorESMhub/NorESM` superproject. Operational depth being filled in.

## Related skills in this org

- [cesm-skill](https://github.com/earth-space-ai/cesm-skill)
- [cam-skill](https://github.com/earth-space-ai/cam-skill)
- [cice-skill](https://github.com/earth-space-ai/cice-skill)
- [ctsm-skill](https://github.com/earth-space-ai/ctsm-skill)

## Acknowledgments

**Gold-standard references for NorESM** (use these to cross-check anything in this skill):
- NorESMhub/NorESM superproject: https://github.com/NorESMhub/NorESM
- NorESM documentation: https://noresm-docs.readthedocs.io/
- BLOM ocean model: https://github.com/NorESMhub/BLOM
- iHAMOCC biogeochemistry: https://github.com/NorESMhub/BLOM (under `hamocc/`)

This scaffold exists only because of the work of other people, and any value
it has is borrowed from theirs.

- The **NorESM developer community** (NORCE, Bjerknes Centre, MET Norway,
  Univ. of Oslo, Univ. of Bergen, NERSC, and partners) for building and
  maintaining [NorESMhub/NorESM](https://github.com/NorESMhub/NorESM), the
  NorESM-specific ocean (BLOM/MICOM), biogeochemistry (HAMOCC/iHAMOCC), and
  aerosol module (OsloAero).
- The **NSF NCAR / ESCOMP community** for the upstream CESM framework that
  NorESM extends, plus the `manage_externals` and `Externals.cfg`
  bootstrapping pattern this skill teaches.
- **Zesen Huang** for [laps-skill](https://github.com/huangzesen/laps-skill),
  the progressive-disclosure layout this repo borrows.

Any errors, oversimplifications, or out-of-date claims in this skill are the
skill author's responsibility, not the upstream community's. This is a
scaffold; operational depth is being filled in iteratively.

## License

MIT (skill content). NorESM has its own license stacked on top of CESM-derived parts; see upstream.
