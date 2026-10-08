# TSD Rally – aplicația (versiunea 0.4.0, pasul 4)

Conținut: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`.

## Publicare pe GitHub Pages (o singură dată)

1. Pe github.com: **New repository**, numele `tsd-app`, **Public**, apoi **Create repository**.
2. Pe pagina depozitului nou: link-ul **uploading an existing file**. Trage cele 5 fișiere (fișierele, nu folderul), apoi **Commit changes**.
3. **Settings → Pages**. La *Source* alegi **Deploy from a branch**, branch **main**, folder **/ (root)**, apoi **Save**.
4. După un minut sau două, aplicația e la `https://NUMELE-TĂU.github.io/tsd-app/`.

## Instalare pe telefon

1. Deschide adresa în **Chrome**, cu internet.
2. Meniul **⋮ → Adaugă pe ecranul de pornire** (sau **Instalează aplicația**).
3. Pornește-o de pe ecranul principal: se deschide pe tot ecranul, în landscape.

## Actualizare

Încarci fișierele noi peste cele vechi (aceleași nume), apoi **Commit changes**.
Pe telefon, cu internet, deschizi aplicația de două ori: prima dată descarcă versiunea nouă, a doua oară o folosește.
Versiunea apare în **☰ → Setări**.

## Ce poți testa acum (cu simulatorul)

- **☰ → Sursă → Pornește simulatorul**, apoi START de pe ecran.
- Viteza din glisor; T_gen, D_gen și mediile curg (cu k = 1).
- **Buton cutie**: un RESTART venit de la „cutie”, ca de la switch.
- **Semnal pierdut 10 s**: GPS trece pe EST, distanța continuă. **40 s**: după 30 s distanța se oprește.
- **Repornire cutie**: distanța totală continuă (lipsesc doar cele 1,5 s de oprire).
- **Pierde următorul eveniment**, apoi **Buton cutie**: aplicația observă lipsa și cere REPLAY.
- **☰ → Date brute**: pachetele decodate, rata (10/s), pachetele pierdute, evenimentele și comenzile (autostart, REPLAY, prag).
- **Fără internet**: după o deschidere cu internet, închide aplicația, pune telefonul în modul avion și deschide-o din nou.

Abaterile, BACK, ±10 m, modul PROBĂ/SEGMENT și k vin la pasul 5.
