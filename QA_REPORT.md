# V17 QA Report

## Release status

**V17 package QA: PASS for automated repository/regression checks.**

## Checks executed

- JavaScript syntax check for `app.js`: PASS
- JavaScript syntax check for `app-bundled.js`: PASS
- V17 smoke suite: PASS
- taxonomy model suite: PASS
- FY 2024-25 MCA-validated XML regression: PASS

## V17 defects addressed

### Filing tabs
All 47 ELRs remain present in the taxonomy model. Navigation is no longer dependent on profile completion. The V17 package preserves the V16/V15 table and typed-dimension model.

### Cash-flow method separation
The imported `TypeOfCashFlowStatement` fact is recognized when present. The profile records Direct Method or Indirect Method and the opposite cash-flow filing tab is intentionally inactive. Generation filters out the inactive method.

### Save reliability
The persisted project snapshot excludes static taxonomy/rule arrays, reducing browser-storage pressure. IndexedDB is used as a fallback when localStorage cannot accept the project. Automatic debounced persistence remains enabled.

### Busy/processing UI
A blocking overlay with elapsed time is used for previous-year XML import, tab pre-scrutiny and Run All Checks.

## Regression fixture

The FY 2024-25 validated XML fixture used by the regression suite contains:

- 413 contexts
- 3,939 fact occurrences
- 61 typed members

The fixture continues to parse and satisfy the repository's expected taxonomy/context/unit/decimal checks.

## Not claimed by this QA report

This report does not certify that V17-generated instances pass the official MCA Validator V5.1. That remains an external acceptance step requiring the generated instance to be loaded into the MCA validator and any reported errors/warnings to be resolved.
