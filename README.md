# TSD Rally – aplicația (versiunea 0.6.3, pasul 6)

Conținut: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`.

## Actualizare

Încarci cele 5 fișiere peste cele vechi pe GitHub (**Add file → Upload files**, aceleași nume), apoi **Commit changes**.
Pe telefon, cu internet, deschizi aplicația de două ori. În **☰ → Setări → Despre** trebuie să scrie **0.6.3**.

(Prima publicare, dacă e cazul: depozit public `tsd-app`, încarci fișierele, apoi **Settings → Pages → Deploy from a branch → main → / (root) → Save**.
Adresa: `https://NUMELE-TĂU.github.io/tsd-app/`. Pe telefon: Chrome → **⋮ → Adaugă pe ecranul de pornire**.)

## Nou în 0.6.3

- **Abaterea pornește pe SEGMENT**, la prima pornire și după fiecare RESET. Butonul o comută în continuare pe PROBĂ.
- **T_dev a dispărut de pe ecran** (apare deja în bară); V_imp, V_inst și D_dev sunt mai mari.
- **Butonul START devine MARK** după start (în loguri: tipul „MARK”, în loc de „RESTART”).
- **Fixurile suplimentare ale telefonului se ignoră**: Android trimite uneori un fix în plus între cele de 1/s, adesea cu viteza 0 în mers. Acum nu mai fac V_inst să sară la 0.

## Nou în 0.6.2

- **Filtru de salturi pentru GPS-ul telefonului**: o citire cu precizie mai slabă de 20 m nu se folosește. Aplicația păstrează ultima viteză validă cel mult 30 s și afișează „EST” lângă precizie, sus. Pe loc, cu semnal slab, distanța nu mai crește din salturi.
- **Accelerometrul e înregistrat în logul continuu** (nu e folosit la calcule): numărul de citiri, frecvența, media, abaterea standard și amplitudinea, pe fiecare rând.
- **Viteza brută a telefonului** e înregistrată separat (`tel_v_brut_kmh`) de cea folosită (`v_kmh`), ca să se vadă ce a filtrat aplicația.
- **Modelul telefonului** apare în lista de loguri și în primul rând al CSV-ului de evenimente, ca să poți compara aparatele.

## Testul cu mai multe telefoane

Pe fiecare telefon, în aceleași condiții (ideal toate odată, pe același suport):

1. ☰ → Sursă → **Folosește GPS-ul telefonului**, apoi **START** (logul se înregistrează doar după START).
2. **5 minute pe loc, afară**, cu motorul pornit.
3. **O tură scurtă** cu câteva opriri complete (și, dacă se poate, o porțiune în coloană, la pas).
4. **RESET**, apoi ☰ → Loguri → **Continuu** (și **Evenimente**), trimise mai departe.

Din fișiere se vede, pentru fiecare telefon: cât de des dă poziții, cât sare viteza pe loc, câtă distanță falsă adună oprit și dacă accelerometrul deosebește oprirea cu motorul pornit de mersul la pas.

## Ce e nou în 0.6.0

- **Doar telefonul**: ☰ → Sursă → **Folosește GPS-ul telefonului**. Merge fără cutie. Precizia GPS apare sus (de exemplu „±5 m”).
- **Rezervă**: cu cutia conectată, GPS-ul telefonului merge în paralel. Dacă cutia nu trimite date peste 1 s, distanța continuă din telefon („TELEFON (rezervă)” sus) și se reglează când cutia revine.
- **Proba se salvează**: dacă aplicația se închide sau telefonul repornește, la redeschidere proba continuă. Alegi din nou sursa din ☰ → Sursă. Cu cutia, distanța parcursă între timp vine din odometrul cutiei; doar cu telefonul, se estimează în linie dreaptă.
- **Loguri**: ☰ → Loguri. Un log începe la START și se închide la RESET. „Evenimente” și „Continuu” se salvează ca CSV (în Descărcări); butonul ⇪ le trimite direct (e-mail, WhatsApp etc.). CSV-ul folosește „;” și virgulă zecimală, pentru Excel în română.
- **Autostart**: ☰ → Probă. Cu cutia îl face cutia; doar cu telefonul îl face aplicația, pe ceasul telefonului.
- **Calibrare**: ☰ → Probă. „Început” la reperul de start al tronsonului, „Sfârșit” la reperul final, introduci distanța oficială în km, apoi **Aplică k** (doar înainte de START).
- **Ceas**: ☰ → Setări. Ora aplicației apare mare, cu zecimi, chiar acolo; offset în pași de 0,1 s și 1 s, aliniat cu time.is.
- **Clicker Bluetooth**: ☰ → Setări → **Învață tasta**, apoi apeși butonul clickerului. De atunci acea tastă dă START/MARK; celelalte sunt ignorate.
- **START mai precis**: momentul apăsării e cel în care atingi ecranul, nu cel în care ridici degetul.

## Primul test live (doar cu telefonul)

Navigatorul operează telefonul, nu șoferul.

1. Telefonul pe suport, cât mai sus pe parbriz, la încărcător. Ecranul rămâne aprins singur.
2. ☰ → Sursă → **Folosește GPS-ul telefonului**. Permiți localizarea (precisă). Aștepți ca precizia de sus să scadă sub 10 m.
3. ☰ → Setări → Ceas: aliniezi cu time.is pe alt telefon (opțional pentru test).
4. **Calibrare pe borne**: ☰ → Probă → „Început” în dreptul unei borne kilometrice, „Sfârșit” după 5 borne, distanța oficială 5,000. Notează k-ul, dar nu e obligatoriu să-l aplici. Bornele nu sunt perfect exacte; testul arată ordinul de mărime.
5. **O probă scurtă**: V_imp de exemplu 40,0, START, încearcă să ții T_dev aproape de 0. Fă câteva RESTART-uri cu viteze diferite, încearcă BACK și ±10 m.
6. **Închide aplicația în mers** (din lista de aplicații recente) și redeschide-o: proba trebuie să continue.
7. La final: ☰ → Loguri → „Evenimente” și „Continuu” pentru proba de test. Trimite-mi fișierele: din ele văd cât de des dă telefonul poziții, cât de zgomotoasă e viteza și cât „merge” distanța cu mașina oprită.

## Testul cu simulatorul (rămâne valabil)

☰ → Sursă → **Pornește simulatorul**: Buton cutie, Semnal pierdut 10/40 s, Repornire cutie, Pierde următorul eveniment.
V_imp 50,0 cu simulatorul la 50 km/h: T_dev stă aproape de 0.
