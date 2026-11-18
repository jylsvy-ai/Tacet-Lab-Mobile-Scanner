# Tacet Lab Mobile Scanner

Standalone mobile-first PWA for scanning and reviewing Wuthering Waves Echoes. No backend/account. Echo and Sonata/character catalogs are extracted from the supplied Tacet Lab source ZIP.

## Run / host

Camera access requires HTTPS (GitHub Pages is suitable) or localhost. Upload the entire folder to a GitHub repository and enable Pages, or serve locally with any static server.

## OCR note

Tesseract.js is loaded from jsDelivr. The app shell/catalogs are cached by the service worker; the OCR library and language data require an initial online load. The app still supports manual entry offline after it has loaded. For fully offline OCR, vendor Tesseract.js + `eng.traineddata` locally and point the worker at those files.

## Export

Exports `tacet-lab-mobile-import` version 1, matching `docs/mobile-scanner-import-format.md` from the supplied Tacet Lab project. Every Echo must have `floor(level/5)` substats; for level 25 this is five. The stable collection ID and per-Echo scan IDs are persisted so repeated exports can be safely re-imported.

## Important

OCR is assistive, not authoritative. The user must review every field. Echo name, Sonata, rarity, equipment, main stat and substats are manually confirmable before saving. The importer remains the final validation authority for canonical main-stat values and catalog compatibility.

Collection persistence uses IndexedDB (with localStorage fallback for recovery). The stable collection UUID remains in localStorage so future exports from the same device retain the same collection identity.
