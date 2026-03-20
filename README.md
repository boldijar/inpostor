# Inpostor

Site static pentru un joc de societate pe telefon: adaugi jucători, alegi niște opțiuni, pornești runda și treceți dispozitivul din mână în mână. Nimic de instalat pe server dacă nu vrei — merge și deschis direct din fișier, ideal e totuși un mic server local ca să nu te lovești de CORS sau de cache ciudat.

> **Da, știm că „se scrie altfel”.** Aici e **inpostor** cu **o**, ca să nu ne luăm prea în serios. Cartofii rămân cartofi.

---

## Despre joc (pe scurt)

Toată lumea primește același **cuvânt secret**, în afară de **inpostor** (sau mai mulți). Ăia nu știu cuvântul; trebuie să se prefască că știu, să asculte și să nu iasă în evidență.

Restul sunt **cartofi**: au cuvântul pe ecran și vor să afle cine e inpostorul fără să dea secretul de gol. Clasicul „un cuvânt pe rând”, vot, eliminare, râsete. Regulile detaliate sunt și în `cum-functioneaza.html` din proiect.

---

## Ce face aplicația

| Ce | Unde |
|----|------|
| Listă jucători, Start | `index.html` + `app.js` |
| Config (categorii, câți inpostori, indicii, variante de rundă) | același ecran, panoul de setări |
| Trecerea pe rând: card ținut apăsat ca să vezi rolul | tot acolo |
| Ecran final + dezvăluire lungă la ținut apăsat | panel „done” |

Cuvintele și indiciile vin din **`dtb.json`**: fiecare intrare are `name` (secretul), `categories` (pentru filtre) și `hint` (ce poate vedea inpostorul dacă ai bifat indiciul — scurt, vag, la mișto).

---

## Fișiere utile

- **`index.html`** — jocul propriu-zis  
- **`styles.css`** — tot UI-ul  
- **`app.js`** — logică, localStorage pentru jucători și config  
- **`dtb.json`** — baza de cuvinte  
- **`scripts/inject_dtb.py`** — copiază JSON-ul din `dtb.json` în blocul `<script id="inpostor-dtb-json">` din `index.html` și `cum-functioneaza.html`. După ce editezi baza, rulezi:

```bash
python3 scripts/inject_dtb.py
```

Altfel paginile rămân cu vechea listă înglobată în HTML.

---

## Cum îl vezi local

Varianta simplă: deschizi `index.html` în browser.

Dacă vrei ceva curat:

```bash
cd inpostor   # sau cum ai numit folderul
python3 -m http.server 8080
```

Apoi `http://localhost:8080` — și gata, poți juca. Cartofii să aibă încărcat telefonul.

---

## Licență / folosire

Proiect personal / de petrecere. Fă ce vrei cu el pentru tine și gașca ta; dacă îl împărți mai departe, un link către repo nu strică.

Spor la votat inpostorii și la apărat onoarea cartofilor.
