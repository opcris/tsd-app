# TSD Rally – app (version 0.7.0)

Files: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`.

## Update

Upload the 5 files over the old ones on GitHub (**Add file → Upload files**, same names), then **Commit changes**.
On the phone, with internet, open the app twice. **☰ → Settings → About** must show **0.7.0**.

First publication, if needed: public repository `tsd-app`, upload the files, then **Settings → Pages → Deploy from a branch → main → / (root) → Save**.
Address: `https://YOUR-NAME.github.io/tsd-app/`. On the phone: Chrome → **⋮ → Add to Home screen**.

## New in 0.7.0

- **The interface is in English** (log event types and CSV columns too).
- **Distance · time · average speed calculator** (☰ → Stage): fill in any two, the third is calculated and highlighted. Values keep full precision (12.34 km in 15:00 gives 49.36 km/h, not 49.4).
  - **Speed stage**: the average speed becomes V_imp (normal regularity stage).
  - **Time stage**: drive the distance in exactly the given time. T_int becomes **T_left** (counts down to zero, then shows minus), **D_left** appears next to D_dev, the bottom button shows TIME STAGE and V_imp is locked. MARK restarts the time stage. RESET returns to a speed stage.
- **Start time** (☰ → Stage): type `hh.mm.ss` (dots, colons or just digits: `143500`, `14.35`). With **start automatically** ticked, the stage starts at that time (the box does it with GPS time; without a box, the app does it on the phone clock). Unticked: beeps only, you press START.
- **Beeps**: one per second in the last 10 seconds and a long beep at zero, before the start time and before the end of a time stage. On/off and a test in ☰ → Settings → Sound.
- **Location blocked**: the app now shows the exact steps to allow it (☰ → Source).
- **CSV format** (☰ → Settings → Logs): Excel EU (`;` and `0,5`) or Standard (`,` and `0.5`). The default follows the phone language.

## Earlier features (short)

- Sources: box (Bluetooth), phone GPS only, simulator. With the box, the phone GPS runs in parallel as backup.
- Deviation: plus = late, minus = early. Starts on SEGMENT after every RESET.
- The stage is saved and resumes if the app closes. Logs: ☰ → Logs (Events and Continuous, saved to Downloads or shared with ⇪).
- Calibration (☰ → Stage), clock offset with a live clock (☰ → Settings → Clock), Bluetooth clicker (☰ → Settings).
- Phone GPS filters: readings worse than 20 m are not used (EST), extra fixes between the 1/s ones are ignored.
