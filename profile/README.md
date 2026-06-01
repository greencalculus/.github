<div align="center">

<img src="https://raw.githubusercontent.com/greencalculus/.github/main/profile/assets/greencalculus-logo.png" width="84" height="84" alt="GreenCalculus — integral-and-leaf mark" />

# GreenCalculus

### The traceable reference layer for corporate carbon accounting.

High-precision carbon and environmental calculators for sustainability officers,
engineers, and compliance teams — every result traceable to a published factor and a named standard.

[**greencalculus.com**](https://greencalculus.com) · [Methodology](https://github.com/greencalculus/greencalculus-methodology) · [Standards](https://github.com/greencalculus/greencalculus-standards) · [Live demos](https://greencalculus.github.io/greencalculus-calculator-demo/)

<br/>

![GHG Protocol](https://img.shields.io/badge/GHG_Protocol-Corporate_·_Scope_3_·_LSR_2026-04BF62?style=flat-square)
![IPCC AR6](https://img.shields.io/badge/IPCC_AR6-GWP--100-04BF62?style=flat-square)
![CSRD](https://img.shields.io/badge/CSRD-ESRS_E1-04BF62?style=flat-square)
![SBTi](https://img.shields.io/badge/SBTi-Near--term_·_Net--zero-04BF62?style=flat-square)
![PCAF](https://img.shields.io/badge/PCAF-Financed_Emissions-04BF62?style=flat-square)
![ISO 14064-1](https://img.shields.io/badge/ISO-14064--1-04BF62?style=flat-square)

</div>

---

## Why GreenCalculus

Most carbon calculators hardcode a number and ask you to trust it. We don't. Every figure
we publish resolves to a **versioned emission factor** with a named source and a citable
standard — so a sustainability lead can hand the output to an auditor, and the auditor can
follow it all the way back to the methodology. **Verifiability is the product.**

## What we build

| Layer | What it is | Aligned to |
|---|---|---|
| **Calculators** | Scope 1, 2 & 3 emissions tools across fuels, energy, value chain, finance, and land | GHG Protocol Corporate Standard + Scope 3 |
| **Data layer** | A single versioned source of truth for every emission factor — see below | IPCC AR6 GWP-100 · DESNZ 2024 · DEFRA 2025 · US EPA · Eurostat |
| **Methodology** | Formal documentation of how each calculation works | GHG Protocol · IPCC AR6 · PCAF |
| **Standards** | Citable reference pages mapping each tool to the standard it implements | CSRD/ESRS E1 · SBTi · ISO 14064-1 · LSR (2026) |

## Calculator coverage

Organised as families, not one-offs — each family folds regional and per-asset variants into a single tool:

- **Scope 1** — stationary & mobile combustion, refrigerants, process emissions
- **Scope 2** — location- & market-based electricity, steam, heat, cooling
- **Scope 3** — spend-based (MRIO/EEIO), category 1–15, transport & distribution
- **Financed emissions (PCAF)** — all 7 Part A asset classes, plus facilitated, insurance-associated, and data-quality scoring
- **Land sector (FLAG)** — land-use change, land management, and carbon removals as separate lines
- **Target setting (SBTi)** — near-term Absolute Contraction trajectories and net-zero pathways

## The data layer — one source of truth

Every calculator reads from a **single, versioned, date-anchored factor store** rather than
scattered hardcoded constants. It holds thousands of emission factors and GWP values across
fuels, electricity grids, spend-based EEIO sectors, and AFOLU — each tagged with its source,
year, and GWP basis.

- **Versioned** — factor sets are date-stamped (e.g. `v2025.x`); a value change is a tracked, auditable event
- **Validated** — automated parity checks gate every change, so no calculator silently drifts from the canonical value
- **Single-sourced** — the same factor feeds the on-site calculator and the underlying API, so the math can never disagree with itself
- **Fail-soft** — an unrecognised key degrades visibly, never to a wrong-but-plausible number

This is the difference between a calculator *site* and a carbon-accounting *reference layer*.

## Start here

| Repository | What you'll find |
|---|---|
| 🌐 **[greencalculus-calculator-demo](https://github.com/greencalculus/greencalculus-calculator-demo)** | Open-source, zero-dependency demos — Scope 1 combustion, SBTi targets, FLAG, PCAF financed emissions |
| 📐 **[greencalculus-methodology](https://github.com/greencalculus/greencalculus-methodology)** | Formal methodology, emission-factor datasets, and GHG Protocol alignment documentation |
| 📖 **[greencalculus-standards](https://github.com/greencalculus/greencalculus-standards)** | Open mapping to the global standards we implement — GHG Protocol, Scope 3, LSR 2026, IPCC AR6, ISO 14064-1, CSRD/ESRS E1, SBTi, DEFRA |

## Engineering

- **Zero-dependency Vanilla JS** — no jQuery, no Bootstrap, no build step for the public tools
- **CSS `@layer` architecture** with fluid `clamp()` typography and `tabular-nums` precision rendering
- **`WebApplication` JSON-LD** schema on every calculator for machine-readable provenance
- **Disciplined versioning** — semantic plugin versions and date-anchored factor versions, every value change logged in a public changelog

## How to cite

> GreenCalculus (2026). *[Calculator or methodology title]*. Version *[x]*.
> GreenCalculus.com. `https://greencalculus.com/...` (accessed *YYYY-MM-DD*).

Each calculator and methodology page carries its own version and last-reviewed date for precise citation.

---

<div align="center">

Built and maintained by **[Jeremiah Say](https://greencalculus.com/about/jeremiah-say/)** — Lead Systems Architect
<br/>
GHG Protocol · IPCC AR6 · CSRD/ESRS E1 · SBTi · PCAF

</div>
