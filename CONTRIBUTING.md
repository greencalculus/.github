# Contributing

These are the defaults for every GreenCalculus repository. A repository with its
own `CONTRIBUTING.md` overrides this one — read that instead.

## The most valuable thing you can send us

**A number you think is wrong.** Every factor we publish carries a verification
link showing the publisher, the document and the exact cell it was read from. If
that cell doesn't say what we say it says, we want to know, and we'd rather hear
it in public than have someone quietly stop trusting the data.

Use the **Report a wrong value** issue template. You don't need to be right —
you need to say which cell you read and what you read in it.

**A factor that isn't there** is the second most valuable. The corpus grows from
those requests. Search first (`search()` is keyless), because names differ from
what you'd expect: diesel is filed by fuel and litre, not by vehicle.

## Code

Every repository states its own test command in its README. In general:

```bash
# Python — stdlib only, no dependencies
python -m unittest discover -s tests -v

# JavaScript / TypeScript
npm install && npx tsc --noEmit && npm run build
```

CI runs on every pull request. Open the PR when the tests pass locally; a draft
PR is fine before that.

## Conventions that hold across the org

- **Refuse rather than guess.** Anything we can't answer correctly must say so
  and name the next action. Never return a plausible number under a label that
  doesn't fit it.
- **Every value carries its source.** A figure without a publisher, a document
  and a cell reference is not finished.
- **Error messages are written for the person reading them**, not for a status
  code.
- **No new runtime dependencies** in the client libraries. They are deliberately
  dependency-free.
- **Versions are the release.** Bump the version in the manifest and merge; the
  release workflow publishes what the registry is missing. There are no release
  tags to cut.

## Commit messages

Say what changed and why it was wrong before. The subject line is a sentence, not
a label — `fix: count factors, not listing rows` tells a reader more than
`fix: dedup`.

## Questions

Each repository has Discussions enabled for questions, ideas and show-and-tell.
Security issues go to **security@greencalculus.com**, not to an issue — see
[SECURITY.md](./SECURITY.md).
