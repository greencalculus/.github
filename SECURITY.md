# Security

## Reporting a vulnerability

Email **security@greencalculus.com** with the details and, if you have one, a
proof of concept. Please don't open a public issue for a vulnerability.

We aim to acknowledge within two working days and to keep you updated while we
work on it. If you'd like credit in the fix notes, say so and we'll include you.

## Scope

In scope: everything published under this organisation — the client libraries
and Sheets add-in, the MCP server and its stdio bridge, the open data export and
its build script, the calculators — plus the services they talk to:
`api.greencalculus.com`, `mcp.greencalculus.com` and `verify.greencalculus.com`.

Out of scope: volumetric denial of service, findings from automated scanners
with no demonstrated impact, and reports about missing headers on pages that
serve no user data.

## API keys

Keys look like `gc_live_…`. If one is exposed — in a commit, an issue, a log, a
screenshot — rotate it at
[greencalculus.com/developers](https://greencalculus.com/developers) and let us
know so we can check for misuse.

The corpus reads without a key, so please don't put a key in example code,
notebooks or bug reports. A keyless client is enough to reproduce most things.

## A note on data, not code

A wrong emission factor is not a security issue, but it is the failure we care
most about. Report those in the open with the
**[Report a wrong value](https://github.com/greencalculus/greencalculus-open-data/issues/new?template=wrong-value.yml)**
template — a carbon number that is quietly wrong is worse than one that is
missing, and we would rather be corrected in public than trusted incorrectly.
