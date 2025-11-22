
Creami Gelato – PWA för Ninja Creami Deluxe
==========================================

Detta paket är en liten Progressive Web App (PWA) som kan läggas på hemskärmen
på din iPhone som "Creami Gelato" och köras offline när den väl har laddats en gång.

Filer:
- index.html            Själva appen (UI, logik)
- manifest.json         PWA-manifest (namn, ikon, färger)
- service-worker.js     Service worker som cachar appen för offlinebruk
- apple-touch-icon.png  Ikon (180x180) för iOS/hemskärmen

Viktigt om iOS/PWA och offline
------------------------------
iOS kräver att PWA:er (service workers) laddas från en "säker origin", dvs:
- https://domännamn/...  (GitHub Pages, Netlify, Vercel, egen webbserver etc.)
- eller http://localhost (om du kör en lokal webbserver)

Service workers fungerar **inte** om du öppnar index.html direkt via file://
eller en ren Filer-app-öppning utan någon form av webserver.

Rekommenderat: GitHub Pages (enkelt och gratis)
-----------------------------------------------
1. Skapa ett GitHub-konto (om du inte redan har).
2. Skapa ett nytt repo, t.ex. `creami-gelato`.
3. Lägg in alla filer i root på repot: index.html, manifest.json,
   service-worker.js, apple-touch-icon.png.
4. Aktivera GitHub Pages i repo-inställningarna, "Pages" → Source: `main` branch, `/ (root)`.
5. Efter några sekunder får du en URL i stil med:
   https://ditt-användarnamn.github.io/creami-gelato/

6. Öppna den URL:en i Safari på iPhone.
7. Safari: Dela → "Lägg till på hemskärmen".
8. Starta appen från hemskärmen – därefter är den cachad och funkar offline.

Vad appen gör
-------------
- Du väljer antal burkar sötad kondenserad mjölk (svenska 397 g-burkar).
- Den räknar ut:
  - total sats
  - mjölkbas (grädde + mjölk) med ca 10 % fett
  - rekommenderat antal Ninja Creami Deluxe-burkar
  - gram per burk
  - glukossirap (ca 3,3 % av totalvikt)
  - extraktmängd totalt och per burk
- Den har snabbval för smaker:
  - Vanilj, Jordgubb, Choklad, Polka, Romrussin, Lime, Salt karamell
- Den har checkboxar för mix-ins per burk (russin, choklad, polkagris, pepparkaka, daim m.m.)
  och visar rekommenderade gram per burk samt små tips.

iPhone kortversion – när sidan väl ligger på https://
-----------------------------------------------------
1. Öppna URL:en i Safari (t.ex. GitHub Pages-länken).
2. Tryck på dela-knappen.
3. Välj "Lägg till på hemskärmen".
4. Starta "Creami Gelato" från hemskärmen.
5. Efter första laddningen hanterar service workern caching → appen fungerar
   även om du tappar nät nästa gång du öppnar den.
