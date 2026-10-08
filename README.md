# TSD Rally – aplicația (versiunea 0.5.0, pasul 5)

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

## Nou în 0.5.0: logica probei

- **V_imp**: atingi câmpul galben și scrii viteza. Înainte de START devine viteza primului segment; în probă se aplică retroactiv de la ultimul RESTART.
- **RESTART** (ecran sau „Buton cutie”): segment nou; păstrează viteza până o schimbi.
- **T_dev / D_dev și bara**: plus (roșu, în stânga) = întârziere, minus (galben, în dreapta) = avans. Bara e plină la 30 s.
- **Abatere: PROBĂ / SEGMENT**: cumulat pe toată proba sau doar pe segmentul curent.
- **BACK**: prima apăsare, distanța scade (butonul devine roșu, „BACK activ”); a doua, revine la normal. Timpul curge.
- **−10 m / +10 m**: corecție de distanță.
- **k**: se schimbă doar înainte de START (atingi butonul), între 0,9 și 1,1.
- **RESET**: proba la zero, cu confirmare; V_imp, k și modul rămân.

Încă nu: salvarea probei la repornirea aplicației, logurile CSV, GPS-ul telefonului și clickerul (pasul 6).

## Un test cu rezultat cunoscut

V_imp = 50,0, simulatorul la 50 km/h, START după ce simulatorul a ajuns la viteză: T_dev stă aproape de 0.
Coboară glisorul la 40: T_dev crește (plus, roșu). Urcă la 60: scade spre minus (galben).
