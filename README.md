# Spark Homes Repair Estimator

A mobile-first Progressive Web App for real estate acquisition teams to estimate repair costs during property walkthroughs.

Built as a submission for the Spark Equity Group developer contest.

**Live demo:** https://jahnavid32.github.io/spark-estimator/

---

## What It Does

Agents walk through a property on their phone, check off needed repairs room by room, enter quantities, and the app calculates a running total in real time. At the end of the walkthrough, they export a ZIP file containing a full Excel cost breakdown and all photos taken during the visit.

---

## Features

- 108 repair line items across 19 groups, organized by room
- Multi-room support: add and remove bathrooms, bedrooms, and living areas freely
- Live running cost total that updates on every interaction
- Per-project price overrides and global price schedule via CSV upload
- Progress tracking across all groups
- Photo capture with AI-powered serial number extraction using Claude Vision API
- Deal Analyzer: calculates profit, ROI, and Max Allowable Offer using the 70% rule
- Scope Summary: one-screen overview of all checked items, shareable via clipboard
- ZIP export with Excel breakdown and all photos
- Works offline via service worker
- Installable on Android and iOS home screen as a PWA
- All data stored in localStorage, no backend required

---

## Stack

- Vanilla JavaScript, HTML, CSS, no frameworks, no build step
- Tailwind CSS via CDN
- xlsx-js-style via CDN for Excel export
- JSZip via CDN for ZIP packaging
- Claude Vision API for serial number OCR
- DM Sans and DM Mono via Google Fonts

---

## How to Run

No installation needed. Open the file directly in a browser:

```
open index.html
```

Or serve locally for full PWA and camera support:

```
npx serve .
```

Then open http://localhost:3000 in Chrome or Safari.

---

## How to Use

1. Open the app on your phone
2. Create a new project with the property address
3. Swipe between rooms or tap the tabs at the top
4. Check items that need work and enter quantities
5. Toggle No action needed for groups that are fine
6. Add photos, the app will attempt to extract serial numbers automatically
7. Tap Deal in the header to run the deal analysis
8. Tap Export ZIP when the walkthrough is done

---

## Creative Feature: Deal Analyzer

The repair total alone does not tell an agent whether to make an offer. The Deal Analyzer takes ARV, purchase price, and holding costs alongside the live repair estimate and shows projected profit, ROI, deal health rating, and Max Allowable Offer using the 70% rule. If the purchase price exceeds the MAO, a warning appears immediately. The summary can be shared via clipboard with one tap.

---

## Known Limitations

- OCR requires network access and will not work offline
- Storing many high-res photos in localStorage can hit browser storage limits on older devices
- CDN scripts require an initial network load before the app works fully offline

---

## AI Tools

Built using Claude by Anthropic. Claude wrote the implementation based on the contest brief and official price list. The Deal Analyzer, swipe gestures, haptic feedback, and OCR integration were designed and directed by the submitter. Claude also powers the serial number extraction feature at runtime.
