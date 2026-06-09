# Nakhla – Websites & Tools

Alles statisches HTML. Direkt zu GitHub Pages hochladbar, jederzeit selbst änderbar,
funktioniert auch lokal per Doppelklick.

```
nakhla-website/
├── index.html              → Nakhla Hauptseite        (nakhla-services.de)
├── detailing/index.html    → Yusha Detailing          (…/detailing/)
├── service/index.html      → Klar & Grün              (…/service/)
├── kundenkarte/index.html  → Stempelkarten-Demo + Präsentation (…/kundenkarte/)
├── impressum/index.html    → Impressum (§ 5 DDG)      (…/impressum/)
├── datenschutz/index.html  → Datenschutzerklärung     (…/datenschutz/)
├── qr-codes.html           → QR-Code-Generator (lokal im Browser öffnen)
├── CNAME                   → deine Domain für GitHub Pages
└── README.md
```

---

## 1. Zu GitHub hochladen
1. github.com → **New repository** → Name z. B. `nakhla-website`, **Public**, anlegen.
2. **Add file → Upload files** → kompletten Ordnerinhalt hochladen (mit allen Unterordnern und der `CNAME`).
3. **Commit changes**.

## 2. GitHub Pages einschalten
1. Repo → **Settings → Pages**.
2. Source: **Deploy from a branch**, Branch: **main**, Ordner: **/ (root)** → **Save**.
3. Nach 1–2 Min. online unter `https://DEIN-NAME.github.io/nakhla-website/`.

## 3. Domain nakhla-services.de verbinden
1. **Settings → Pages → Custom domain** → `nakhla-services.de` (die `CNAME`-Datei macht das meist automatisch).
2. Beim Domain-Anbieter im DNS eintragen:
   - **A-Records** (Hauptdomain): `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **CNAME** (www): `www → DEIN-NAME.github.io`
   > IPs bei Bedarf in der offiziellen GitHub-Pages-Doku gegenprüfen.
3. DNS abwarten (paar Stunden), dann **„Enforce HTTPS"** anhaken.

Ergebnis: `…de` (Nakhla), `…de/detailing/`, `…de/service/`, `…de/kundenkarte/`.

---

## 4. PFLICHT vor dem Live-Gang: Rechtstexte ausfüllen
In `impressum/index.html` und `datenschutz/index.html` sind alle Stellen, die DU einsetzen
musst, **orange markiert** (im Code als `<span class="ph">…</span>`):
- **Vollständiger Vor- und Nachname** (ersetzt `Yusha [VOLLSTÄNDIGER NACHNAME]`).
- **USt-IdNr.** falls vorhanden – sonst die Zeile löschen (als Kleinunternehmer nach § 19 UStG).
- Adresse (Alter Teichweg 81, 22081 Hamburg) ist bereits eingetragen.

> Hinweis: Diese Texte sind sorgfältige Vorlagen, aber keine Rechtsberatung.
> Für 100 % Sicherheit einmal durch einen kostenlosen Generator prüfen
> (z. B. e-recht24.de) oder einen Anwalt drüberschauen lassen.

## 5. Google Fonts selbst hosten (empfohlen vor Live-Gang)
Die Seiten laden Schriften von Google. Das ist im Datenschutz ausgewiesen, aber für
maximale DSGVO-Sauberkeit (Stichwort Abmahnungen) sollten die Schriften lokal liegen.
Einfacher Weg: `google-webfonts-helper` (gwfh.mranftl.com) → Schrift wählen → Dateien
herunterladen → in einen `/fonts`-Ordner legen → den `<link …googleapis…>` durch das
mitgelieferte `@font-face`-CSS ersetzen. (Sag Bescheid, dann mache ich das für dich.)

---

## 6. Inhalte ändern
Unten in jeder `index.html` steht ein markierter `CONFIG`-Block:
```js
const CONFIG = {
  whatsapp: "491718198454",     // ohne + und ohne 0
  email: "info@nakhla-services.de",
  siteUrl: "https://nakhla-services.de"   // Ziel des QR-Codes auf der Seite
};
```
Texte/Preise/Überschriften direkt im HTML überschreiben.

**Social-Links anschalten:** im Footer `data-on="0"` → `data-on="1"` setzen und bei
`data-href` deinen echten Link eintragen.

## 7. QR-Codes erzeugen
`qr-codes.html` doppelklicken → vier Codes (3 Seiten + Kundenkarten-Demo) →
URL bei Bedarf anpassen → **Neu erzeugen** → **Download** (hochauflösend, druck-/wallet-tauglich).
Wallet-Anleitung (Pass2U) steht unten auf der Seite.
> Erst hochladen, echte Adresse prüfen, **dann** QR erzeugen.

## 8. Kundenkarten-Demo beim Kunden zeigen
`kundenkarte/index.html` öffnen → Button **„▶ Präsentation"** = Vollbild-Slideshow
(Pfeiltasten/Wischen blättern, Esc beendet). In der Live-Demo den **Ladennamen des Kunden**
eintippen → seine eigene Karte erscheint. „+ Stempel geben" zeigt, wie sie sich füllt.
