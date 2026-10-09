# TSD Rally – app (version 0.7.1)

© 2026 Cristian Popa <op_cris@yahoo.com>

## Licence

- **App and firmware:** [PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) (full text in `LICENSE`). Free to use, change and share for any noncommercial purpose: personal use, hobby, clubs, crews in competition. Selling it, or using it in a paid product or service, needs a separate licence from the author.
- **Documentation and hardware** (manuals, specifications, schematic, PCB and Gerber files): [Creative Commons BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). Credit the author, no commercial use, changed versions under the same licence.
- Everything is provided as is, without any warranty.

Files: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `LICENSE`, `README.md`.

## Update

Upload the files over the old ones on GitHub (**Add file → Upload files**, same names), then **Commit changes**.
On the phone, with internet, open the app twice. **☰ → Settings → About** must show **0.7.1**.

First publication, if needed: public repository `tsd-app`, upload the files, then **Settings → Pages → Deploy from a branch → main → / (root) → Save**.
Address: `https://YOUR-NAME.github.io/tsd-app/`. On the phone: Chrome → **⋮ → Add to Home screen**.

## New in 0.7.1

- **Time stages inside one session.** One START at the start of the leg, one RESET at its end. T_gen and D_gen stay cumulative the whole time, also on the liaisons.
  - ☰ → Stage → distance and time → **Time stage** now *arms* the time stage: the top bar shows **⏱ next** and the button says *starts time stage*.
  - The next **MARK** (screen, clicker, box button) or the automatic start time starts it: T_left, D_left, V_imp locked, deviation on the time stage only.
  - At zero T_left goes negative and keeps counting, so you see how late you are.
  - **MARK during a time stage ends it**: the app goes back to the speed stage with the V_imp from before. The log gets TIME_STAGE_END with T_left and D_left at that moment.
  - **False start:** arm the time stage again (☰ → Stage → Time stage); the next MARK restarts it from zero.
  - Before START: arm it and START starts the session and the time stage together.
  - Speed stage button is refused while a time stage runs (MARK ends it first); with a time stage armed but not started, it cancels the arming.
- **Author and licence** (PolyForm Noncommercial) in ☰ → Settings → About.

## New in 0.7.0

- **The interface is in English** (log event types and CSV columns too).
- **Distance · time · average speed calculator** (☰ → Stage): fill in any two, the third is calculated and highlighted. Values keep full precision (12.34 km in 15:00 gives 49.36 km/h, not 49.4).
  - **Speed stage**: the average speed becomes V_imp (normal regularity stage).
  - **Time stage**: drive the distance in exactly the given time. T_int becomes **T_left** (counts down to zero, then shows minus), **D_left** appears next to D_dev, the bottom button shows TIME STAGE and V_imp is locked. (0.7.1 changes how it starts and ends, see above.)
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
