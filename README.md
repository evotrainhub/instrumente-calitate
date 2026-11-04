# Kano live + Diagrama afinității – instalare

Două aplicații statice (câte un fișier `index.html`), pentru GitHub Pages, cu sincronizare în timp real prin Firebase Realtime Database.

## 1. Testare imediată (fără Firebase)
Deschideți `kano/index.html` sau `afinitate/index.html` în browser. Apare eticheta **„Mod demo local”**: datele se sincronizează doar între taburile aceluiași browser. E suficient pentru a vedea fluxul (un tab = formator, alte taburi = participanți).

## 2. Firebase (o singură dată)
Puteți refolosi proiectul Firebase de la aplicația existentă de diagramă a afinității.
1. Firebase Console → proiectul → **Build → Realtime Database** (dacă nu există, „Create database”, regiunea europe-west1).
2. Tab-ul **Rules** → lipiți conținutul din `database.rules.json` → Publish.
   Regulile deschid doar căile `kano/` și `afinitate/`; restul bazei rămâne neatins.
3. **Project settings → Your apps → Web app** → copiați obiectul `firebaseConfig`.
4. În AMBELE fișiere `index.html`, căutați `const FIREBASE_CONFIG = null;` și înlocuiți `null` cu obiectul copiat (trebuie să conțină `databaseURL`).

## 3. GitHub Pages
Urcați folderele `kano/` și `afinitate/` într-un repository (ex. `evotrainhub/instrumente-calitate`) → Settings → Pages → Deploy from branch.
Linkuri: `.../kano/` și `.../afinitate/`. Zona formatorului: adăugați `?prof` la final.

## Utilizare la curs
- **Formator:** `.../kano/?prof` → „Creează sesiunea” → copiați linkul pentru participanți în chatul Zoom/Teams. Linkul cu `admin=…` este cheia de administrare: păstrați-l.
- **Kano:** bifați „Chestionar deschis”; rezultatele se calculează live. Opțional: „Colectez propuneri de atribute” înainte, „Arată rezultatele participanților” la final. Export CSV pentru Excel.
- **Afinitate (studiul de caz cu conferința internațională, preîncărcat):** 1) participanții intră cu numele, „în comitetul de organizare”; 2) porniți cronometrul (implicit 5 min) – fiecare își vede doar propriile idei, iar dumneavoastră vedeți cine nu a scris încă nimic; 3) la expirare, toate ideile apar deodată pe o singură tablă și grupul întreg le grupează pe categorii; 4) rezultat + export CSV.

## De știut
- Securitate minimă, potrivită pentru exerciții la curs: oricine are codul sesiunii poate scrie în ea; tokenul de admin doar ascunde comenzile din interfață. Nu colectați date sensibile.
- Numele participanților se salvează în Firebase. Pentru conformitate GDPR (dacă vreți să fiți consecventă cu modulul de curs), cereți inițiale sau pseudonime.
- După curs, ștergeți sesiunile din „Setări → Șterge sesiunea”.
