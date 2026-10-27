# lens-to-tensor

A playbook for ingesting camera data into vision models: what a camera's
characteristics do to a model's output, measured rather than assumed.

Owner: Teyr. Readers: Visual AI.

## How to use it

- **Picking a camera or a preprocessing setting?** Search `playbook/` for the model or
  the camera property you care about. Each entry states one claim, the conditions it
  was measured under, and where the evidence lives.
- **Trust the `Status` line.** `verified` means measured and reproducible from the
  linked evidence. `inferred` means it follows from measurements but was not tested
  directly. `candidate` means it is a working hypothesis.
- **Something contradicts an entry?** Open an issue with what you saw. A contradicted
  entry is more useful than a confident one.

## Layout

```text
playbook/   one entry per claim, numbered (see playbook/TEMPLATE.md)
tools/      capture and measurement scripts that produce entry evidence
```

Data stays out of the repo. Entries point to where the data lives.

## Adding an entry

Copy `playbook/TEMPLATE.md` to `playbook/NNNN-short-claim.md` with the next free number.
Fill every field. An unknown field says `unknown`, not blank.
