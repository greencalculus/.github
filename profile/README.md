<div align="center">

<img src="https://raw.githubusercontent.com/greencalculus/.github/main/profile/assets/greencalculus-logo.png" width="84" height="84" alt="GreenCalculus — integral-and-leaf mark" />

# GreenCalculus

### The carbon API that hands back the source with the number.

16,000+ sourced greenhouse-gas emission factors and audit-traced calculations —
every value returned with the publisher, the exact cell it was read from, and the data
version it was read at. So your users get a figure an auditor can follow, not a guess.

[**Get a free key**](https://greencalculus.com/developers/) · [SDKs](https://github.com/greencalculus/greencalculus-sdk) · [MCP](https://github.com/greencalculus/greencalculus-mcp) · [Open data](https://github.com/greencalculus/greencalculus-open-data) · [Benchmark](https://github.com/greencalculus/greencalculus-benchmark) · [greencalculus.com](https://greencalculus.com)

<br/>

[![PyPI](https://img.shields.io/pypi/v/greencalculus?label=pypi)](https://pypi.org/project/greencalculus/)
[![npm](https://img.shields.io/npm/v/greencalculus?label=npm)](https://www.npmjs.com/package/greencalculus)
![MCP](https://img.shields.io/badge/MCP-12_tools-04BF62?style=flat-square)
![Free tier](https://img.shields.io/badge/free%20tier-no%20card-04BF62?style=flat-square)
![GHG Protocol](https://img.shields.io/badge/GHG_Protocol-Corporate_·_Scope_3_·_LSR_2026-04BF62?style=flat-square)
![IPCC AR6](https://img.shields.io/badge/IPCC_AR6-GWP--100-04BF62?style=flat-square)
![PCAF](https://img.shields.io/badge/PCAF-Financed_Emissions-04BF62?style=flat-square)

</div>

---

## Try it without signing up

The corpus is **open to read — no API key**:

```bash
curl "https://api.greencalculus.com/v1/factors?key_prefix=grid.gbr.electricity.location_based&limit=1"
```

```jsonc
{
  "key":   "grid.gbr.electricity.location_based",
  "factor": { "value": 0.13096, "unit": "kg CO2e per kWh", "gwp_set": "AR5_100" },
  "source": { "id": "DEFRA_2026", "cell_ref": "'UK electricity'!E25", "retrieved": "2026-06-18" },
  "licence": { "name": "Open Government Licence v3.0", "redistributable": true },
  "citation": { "proof_url": "https://verify.greencalculus.com/grid.gbr.electricity.location_based@2026.188" }
}
```

That `proof_url` is a permanent page showing the publisher, the document, the exact
cell and whether the value may be republished — a link your own reader can check.

Searching the corpus is keyless too:

```ts
import { GreenCalculus } from "greencalculus";      // npm install greencalculus

const gc = new GreenCalculus();                     // no key
const { factors } = await gc.search("diesel litre");
console.log(factors[0].key, factors[0].factor.value);   // fuels.can.diesel.litre 2.68901
```

A [**free key**](https://greencalculus.com/developers/) (no card) adds the seven
calculation engines and `as_of=` version pinning.

## What developers get

| Surface | Where |
|---|---|
| **REST API** | `api.greencalculus.com/v1` — factors, search, resolve, and 7 calculation engines. [Docs & keys](https://greencalculus.com/developers/) |
| **Python & JS/TS SDKs** | [`greencalculus-sdk`](https://github.com/greencalculus/greencalculus-sdk) — `pip install greencalculus` · `npm install greencalculus` |
| **MCP server** | [`greencalculus-mcp`](https://github.com/greencalculus/greencalculus-mcp) — remote at `mcp.greencalculus.com`, or stdio/Docker. 12 tools |
| **Google Sheets** | `=GC_FACTOR("grid.gbr.electricity.location_based")` — [add-on + template](https://github.com/greencalculus/greencalculus-sdk/tree/main/sheets) |
| **Postman** | [Importable collection](https://github.com/greencalculus/greencalculus-sdk/tree/main/postman) |

**Seven calculation engines** — GHG Protocol activity, electricity (location- & market-based),
freight, business travel, spend-based EEIO, embodied carbon (EN 15978), and PCAF financed
emissions. Each returns the full working and a deterministic receipt hash, never just a total.
`as_of=` pins any factor to a past data version, so a figure re-runs identically in an audit.

### Agent-native

```json
{ "mcpServers": { "greencalculus": {
  "url": "https://mcp.greencalculus.com",
  "headers": { "Authorization": "Bearer gc_live_..." } } } }
```

Discovery and the keyless tools work without a key. `explain_absence` answers *why* a
factor you expected isn't there — usually the real question behind "do you have X?".

---

## Why an agent needs this: the benchmark

Ask a language model for an emission factor with no tools and it will usually give you
one. [**`greencalculus-benchmark`**](https://github.com/greencalculus/greencalculus-benchmark)
measures how often that number is right — and how often the model names the wrong source
for it. 467 questions, 45 sections, 75 publishers, generated deterministically against
sourced ground truth.

**Five models, 467 questions, no tools:**

| Model | Answered | Right *when it answered* | Right source, wrong number |
|---|---:|---:|---:|
| Gemini 3.1 Pro | 77 | **65.2%** | 35.3% |
| Grok 4.6 | 144 | 62.1% | 31.6% |
| GPT-5.5 | 326 | 58.2% | 41.0% |
| Claude Opus 5 | 430 | 45.7% | 54.1% |
| Gemini 3.6 Flash | 404 | 41.9% | 58.8% |

The more a model answers, the less each answer is worth — and the last column sorts with
talkativeness. A model that cites DEFRA for an EPA figure is more dangerous than one that
cites nothing, because the citation is what makes a reader stop checking.

**Connect GreenCalculus and it goes away.** 90 questions, paired, same model with and
without two keyless lookup tools:

| | Without tools | With GreenCalculus |
|---|---:|---:|
| Claude Opus 5 — within 10% | 37.1% | **98.7%** |
| GPT-5.5 — within 10% | 50.0% | **100.0%** |

About **+61 points** for both, at 1.0–1.6 tool calls per question. The model isn't handed
the answer — it searches, picks the factor and reads the value, so this measures the
integration, not a rigged prompt. [Full write-up, caveats, and the log of the scorer's own
six bugs](https://github.com/greencalculus/greencalculus-benchmark/blob/main/FINDINGS.md).

## What's in the corpus: open data

[**`greencalculus-open-data`**](https://github.com/greencalculus/greencalculus-open-data)
publishes the coverage map — **16,673 factors from 137 publishers**, each row with its key,
section, unit, gas, GHG Protocol scope, publisher, licence, and whether it may be
republished. Generated from the live API, nothing hand-maintained.

- **15,347 factors / 75 sources** carry a licence that permits republication — OGL, CC BY 4.0, Etalab, US public domain, Eurostat reuse.
- **1,326 factors / 62 sources** do not, and the reason is the publisher's own: paid standards, NonCommercial or NoDerivatives terms, viral share-alike, or no grant found.

**No factor values** — it's our metadata about what the corpus covers, so it's publishable
regardless of upstream terms and you can use it freely to answer "is there a factor for X?"
without worrying about anyone's licence. Values come from the API, keyless.
[`LICENCES.md`](https://github.com/greencalculus/greencalculus-open-data/blob/main/LICENCES.md)
carries every source, its licence, and the attribution line that licence requires — plus
every excluded source with the publisher's stated reason, verbatim.

---

## The data layer behind all of it

One **versioned, date-anchored factor store** — not scattered hardcoded constants. The same
factor feeds the public calculators, the API, the SDKs and the MCP server, so the maths can
never disagree with itself.

- **Versioned** — factor sets are date-stamped (`2026.188`); a value change is a tracked, auditable event
- **Validated** — automated parity checks gate every change, so no surface silently drifts from the canonical value
- **Traceable** — every value carries its publisher, cell reference, licence, uncertainty and GWP basis
- **Fail-soft** — an unrecognised key degrades visibly, never to a wrong-but-plausible number

## Calculators & standards

Free public tools at [greencalculus.com](https://greencalculus.com), organised as families
rather than one-offs — each folds regional and per-asset variants into a single tool:

- **Scope 1** — stationary & mobile combustion, refrigerants, process emissions
- **Scope 2** — location- & market-based electricity, steam, heat, cooling
- **Scope 3** — spend-based (MRIO/EEIO), categories 1–15, transport & distribution
- **Financed emissions (PCAF)** — all 7 Part A asset classes, plus facilitated, insurance-associated, and data-quality scoring
- **Land sector (FLAG)** — land-use change, land management, and removals as separate lines
- **Target setting (SBTi)** — near-term Absolute Contraction trajectories and net-zero pathways

Aligned to GHG Protocol Corporate & Scope 3 · LSR (2026) · IPCC AR6 GWP-100 · ISO 14064-1 ·
CSRD/ESRS E1 · SBTi · PCAF.

## Repositories

| Repository | What you'll find |
|---|---|
| 🔌 **[greencalculus-sdk](https://github.com/greencalculus/greencalculus-sdk)** | Official Python & JS/TS clients, plus Sheets and Postman |
| 🤖 **[greencalculus-mcp](https://github.com/greencalculus/greencalculus-mcp)** | MCP server — 12 tools, remote or stdio |
| 📊 **[greencalculus-benchmark](https://github.com/greencalculus/greencalculus-benchmark)** | How wrong LLMs are about emission factors, and how much tools fix it |
| 🗂 **[greencalculus-open-data](https://github.com/greencalculus/greencalculus-open-data)** | 16,673-factor coverage map with per-publisher licensing |
| 🌐 **[greencalculus-calculator-demo](https://github.com/greencalculus/greencalculus-calculator-demo)** | Zero-dependency demos — Scope 1, SBTi, FLAG, PCAF |
| 📐 **[greencalculus-methodology](https://github.com/greencalculus/greencalculus-methodology)** | Formal methodology and GHG Protocol alignment documentation |
| 📖 **[greencalculus-standards](https://github.com/greencalculus/greencalculus-standards)** | Open mapping to the standards we implement |

## How to cite

Every factor response ships a ready-made citation line:

> UK grid electricity — location-based (generation). UK Government GHG Conversion Factors
> 2026 — Department for Energy Security and Net Zero (DESNZ), cell `'UK electricity'!E25`,
> retrieved 2026-06-18. via GreenCalculus data version 2026.188.

For a calculator or methodology page:

> GreenCalculus (2026). *[Title]*. Version *[x]*. GreenCalculus.com.
> `https://greencalculus.com/...` (accessed *YYYY-MM-DD*).

---

<div align="center">

Built and maintained by **[Jeremiah Say](https://greencalculus.com/about/jeremiah-say/)** — Lead Systems Architect
<br/>
GHG Protocol · IPCC AR6 · CSRD/ESRS E1 · SBTi · PCAF

</div>
