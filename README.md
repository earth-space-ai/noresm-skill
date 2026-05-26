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

## License

MIT (skill content). NorESM has its own license stacked on top of CESM-derived parts; see upstream.
