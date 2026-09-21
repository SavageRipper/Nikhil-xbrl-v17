# MCA C&I XBRL Workbench V17

GitHub Pages-ready, client-side XBRL preparation workbench for the MCA C&I 2016 taxonomy model.

## V17 focus

V17 is a reliability release based on the V16 package. It fixes the main defects encountered during V16 use:

- filing tabs remain navigable without requiring a completed profile;
- CIN/DIN/PAN/DOB and other profile validation remain part of checks;
- imported Direct/Indirect cash-flow data is separated using the taxonomy's `TypeOfCashFlowStatement` fact;
- automatic browser persistence is smaller and more reliable, with IndexedDB fallback;
- previous-year XML import, tab pre-scrutiny and Run All Checks show a blocking loading state;
- the taxonomy-driven dimensional/table model and typed dimensions from V15/V16 are retained.

## Repository structure

```text
.
├── .github/workflows/qa.yml
├── index.html
├── styles.css
├── app.js
├── app-bundled.js
├── TAXONOMY_MODEL.json
├── REFERENCE_TAXONOMY_2016-03-31.xlsx
├── REFERENCE_BUSINESS_RULES_CI_2016_V1.3.xls
├── Applicable_ELR.csv
├── TAXONOMY_TABLE_CATALOG.csv
├── Mandatory_Line_Items.csv
├── Generic_rules.csv
├── Specific_rules_for_elements.csv
├── Parent_Child_Exempt_Calculation.csv
├── Exempt_Child_Member_Dimension.csv
├── Exempt_parent_member_Dimension.csv
├── USER_GUIDE_XBRL_TERMS.md
├── V15_*.md
├── V16_*.md
├── V17_CHANGELOG.md
├── V17_REGRESSION_REPORT.md
├── QA_REPORT.md
└── tests/
    ├── smoke.mjs
    ├── model.mjs
    └── xml-regression.py
```

## Running locally

No build server is required for the bundled application. The simplest local test is to serve the folder over HTTP because the unbundled app loads JSON resources with `fetch`.

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080/`.

The GitHub Pages deployment can use the bundled `app-bundled.js` directly.

## QA

```bash
node --check app.js
node --check app-bundled.js
node tests/smoke.mjs
node tests/model.mjs
python3 tests/xml-regression.py /path/to/mca-validated-instance.xml
```

## MCA validation

The workbench performs local structural/business-rule checks, but those checks are not a substitute for MCA Validator V5.1. A generated instance should still be loaded into the official MCA validation tool, validated, pre-scrutinized, and reviewed in PDF before filing.

## Privacy / authentication

V17 has no login requirement and is client-side. Filing data is kept in the browser unless the user explicitly downloads a project/XML file. The application does not bypass MCA CAPTCHA/session controls or perform unauthorized MCA scraping.
