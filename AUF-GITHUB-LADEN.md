# Auf GitHub laden — die Schritte

Dieser Ordner ist so aufgebaut, dass er direkt ein GitHub-Projekt sein kann.
Was noch fehlt, ist dein Zugang — an Passwörter und Token darf ich nicht,
diesen Teil musst du selbst machen. Zwei Wege, beide funktionieren.

## Weg A — im Browser, ohne Terminal

1. Auf github.com einloggen, oben rechts auf **+** → **New repository**
2. Name: `stauplan-ladespiel` · Beschreibung: „Browserspiel: Bulk Carrier beladen ohne Schlagseite"
3. **Private** wählen, solange die Veröffentlichung nicht mit Lars geklärt ist
4. Anlegen, dann auf der leeren Seite **uploading an existing file** anklicken
5. Aus dem Finder `index.html`, `wordpress-block.html`, `README.md` und den Ordner
   `archiv` ins Browserfenster ziehen, unten auf **Commit changes**

Fertig. `AUF-GITHUB-LADEN.md` und `.gitignore` brauchst du dort nicht mitzuladen.

## Weg B — im Terminal

Repo wie in Weg A anlegen (Schritt 1–3), dann im Terminal:

```
cd ~/Documents/Cowork/"Global Shipping"/GSL_Stauplan-Spiel
git init
git config user.name "Daria Streblow"
git config user.email "DEINE-GITHUB-MAILADRESSE"
git add .
git commit -m "Stauplan v3: Ladespiel, eigenständige Fassung und WordPress-Block"
git branch -M main
git remote add origin https://github.com/DEIN-NAME/stauplan-ladespiel.git
git push -u origin main
```

Zwei Stellen anpassen: `DEINE-GITHUB-MAILADRESSE` und `DEIN-NAME`.
Beim Push fragt GitHub nach einem Personal Access Token statt eines Passworts —
den legst du unter Settings → Developer settings → Personal access tokens an.

**Hinweis zur Mailadresse:** Was du bei `user.email` einträgst, steht später
öffentlich in der Commit-Historie. GitHub bietet unter Settings → Emails eine
Wegwerfadresse der Form `1234567+name@users.noreply.github.com` an — die ist
für öffentliche Repos die bessere Wahl.

## Spielbare Adresse (nur bei öffentlichem Repo)

Repo → Settings → Pages → Source: `main`, Ordner `/ (root)`, speichern.
Nach ein bis zwei Minuten läuft das Spiel unter
`https://DEIN-NAME.github.io/stauplan-ladespiel/`.
Bei einem privaten Repo geht das im Gratistarif nicht.

## Vorher überlegen

Das Spiel trägt GSL-Logo, Firmennamen und die Bremer Adresse in der Fußzeile.
Öffentlich heißt: für jeden auffindbar, auch für Suchmaschinen. Solange Lars den
Einsatz nicht freigegeben hat, ist **privat** die richtige Einstellung —
umstellen kannst du das später mit zwei Klicks.
