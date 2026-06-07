# US Auto Insurance Requirements — D11 Release Candidate

This clean deployment package contains only the production website files:

- `index.html`
- `reference-icon.png`
- `README.md`
- `Auto_Insurance_Requirements.xlsx`

## Local test setup

1. Extract this ZIP.
2. Open Command Prompt or PowerShell in the extracted folder.
3. Run:

```bash
python -m http.server 8000
```

4. Open:

```text
http://localhost:8000
```

## Required manual regression tests

Test states: FL, TX, NY, CA, WA, WY, NM, ND, RI.

For each state, confirm:

- Minimum Insurance Requirements display BI and PD.
- PIP, UM/UIM, and SOL fields display where workbook data exists.
- Policy Disclosure section appears.
- Claims Handling Deadlines section appears.
- Source links are visible and clickable.
- State dropdown and map click load the same information.
- No console errors appear in browser DevTools.

## GitHub Pages upload

Replace the existing production files with the four files in this ZIP. Do not upload old audit reports or working documents into the live site package.


## D13 Link/Citation Fix
- Restored original working hyperlinks for the Minimum Requirements source cells from the known-good workbook.
- Added `Minimum_Source_URLs` and `D13_Link_Citation_Audit` to prevent silent missing source-link regressions.
- Root cause: earlier workbook processing preserved citation text but stripped hyperlink relationships from the older minimum-source cells, causing the website to lack usable targets for those links.


D15 note: If replacing a prior local test build at the same localhost URL, hard-refresh the browser (Ctrl+F5) or clear site cache. This package also includes a self-contained Source_Index parser so the prior rawObjectsFromSheet regression cannot block workbook loading.


## D17 tablet/mobile panel-only fix

At tablet and phone widths, the map is intentionally hidden and the site uses the information panel only. Use the search box or state dropdown to navigate. Desktop layout is unchanged. Source links remain tappable and open in a new browser tab.


## D18 Tablet/Mobile Layout Fix

At viewport widths of 1100px and below, the site intentionally hides the map and uses the information panel as the full layout. Use the search box or state dropdown to navigate. Desktop map layout remains unchanged above 1100px.


## D19 Tablet Panel Fix

At 1100px and below, the site now forces panel-only mode: map/sidebar are hidden and the state selector/detail panel uses the full usable width. This final CSS override appears after earlier responsive rules so tablet emulation at 820x1180 cannot fall back to the desktop two-column layout.
