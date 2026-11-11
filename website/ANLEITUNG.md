# Website veröffentlichen

## 1. Platzhalter ersetzen (mit dem Editor, Suchen & Ersetzen)
In **index.html**:
| Platzhalter | Ersetzen durch |
|---|---|
| `LEMON_LINK_JAHR` | Checkout-Link „Pro Jahr“ aus Lemon Squeezy |
| `LEMON_LINK_LIFETIME` | Checkout-Link „Lifetime“ |
| `MICROSOFT_STORE_LINK` | Link zur Store-Seite (oder den Knopf löschen, solange es keinen gibt) |
| `SUPPORT_EMAIL` | deine Support-Adresse |
| `29 €` / `79 €` | deine echten Preise (Abschnitt „Preise“) |
| `Version 1.0.4 · 38 MB` | aktuelle Version und Größe des Installers |

In **impressum.html** und **datenschutz.html**: alle Angaben in [eckigen Klammern]
ausfüllen und den gelben „ENTWURF“-Absatz löschen. Am einfachsten zuerst in
`assets/impressum.md` / `assets/datenschutz.md` der App ändern – dann sind App
und Website gleich (ich wandle sie dir gern wieder um).

In **version.json**: Versionsnummer und Download-Link.

## 2. Dateien ablegen
- `bilder/`: Screenshots `1_uebersicht.png` … `6_buchungen.png`
  (aus `build\screenshots`, Nr. 1 selbst aufnehmen). Fehlende Bilder blendet
  die Seite automatisch aus.
- `download/FinanzImmo_Setup.exe`: den Installer aus `release\dist` (umbenennen).
- Die beiden `LIES_MICH.txt` danach löschen.

## 3. Hochladen – kostenlos mit Netlify (am einfachsten)
1. https://app.netlify.com/drop öffnen (kostenloses Konto anlegen).
2. Den **ganzen Ordner `website`** ins Browserfenster ziehen. Fertig – du
   bekommst eine Adresse wie `https://finanzimmo-abc.netlify.app`.
3. Für Updates: im Netlify-Projekt → *Deploys* → Ordner erneut hineinziehen.
4. Eigene Domain: *Domain management* → *Add a domain* (z. B. finanzimmo.de bei
   einem Anbieter wie INWX, Strato oder IONOS kaufen und die angezeigten
   DNS-Einträge dort eintragen). HTTPS richtet Netlify automatisch ein.
Die Datei `_headers` setzt automatisch Sicherheits-Header und sorgt dafür, dass
`version.json` nie zwischengespeichert wird.

Alternative: GitHub Pages (Repository → Settings → Pages) – dann wird
`_headers` ignoriert, sonst funktioniert alles gleich.

## 4. In der App eintragen
In `fints.json`:
```
"UPDATE_URL": "https://deine-domain.de/version.json"
```
In `lib/sync/sync_config.dart`:
```
static const String proInfoUrl = 'https://deine-domain.de/#preise';
```
Danach neu bauen.

## 5. Vor dem Start prüfen
- [ ] Alle Links klicken (Kaufen, Download, Impressum, Datenschutz, Support)
- [ ] Am Handy ansehen
- [ ] Impressum/Datenschutz rechtlich prüfen lassen
- [ ] Lemon Squeezy: Website-Adresse im Store-Profil eintragen (wird bei der
      Freischaltung des Shops geprüft)
