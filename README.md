# Proportional meter: inferred total label

Synthetic local demonstration of Carbon Charts @carbon/charts 1.27.25 at upstream commit 4baa87bb1b5aba5e1a16b3a7bd8cf9c548afd894.

The data contain two groups with values 4 and 6. The options set `meter.proportional: { unit: "units" }` and omit the optional `total`. The default total label is `undefined units total` before the patch and `10 units total` after it. Updating the values to 7 and 8 updates the patched total label to 15.

The before/after screenshots use Chromium 151.0.7922.34 and the same synthetic data and configuration. Firefox 153.0 and WebKit 26.5 were also tested. Each engine checks omitted, explicit 100, custom formatter and explicit 0 totals.

The source patch changes only the default total-label formatting expression to `numberFormatter(total ?? totalValue, localeCode)`. Custom total formatters, explicit totals (including 0), chart geometry and breakdown labels keep their existing behavior.

Validation: original 3 failed / 3 passed; patched 6 passed; 12 browser scenarios per phase; ESM/UMD builds pass; formatting and lint pass (13 pre-existing warnings). Type checking returns the same two baseline diagnostics in axes/ruler.ts and axes/toolbar.ts. An independent AI-assisted review was used; execution results came from local tools.
