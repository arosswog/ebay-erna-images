# Bilder hochladen - Anleitung fuer Erna

## Einmalig: Repo lokal clonen

```bash
git clone https://github.com/arosswog/ebay-erna-images.git
cd ebay-erna-images
```

Falls nach Zugangsdaten gefragt wird: Username = arosswog, Passwort = GitHub
Personal Access Token (nicht das echte Passwort). Token liegt in
~/.hermes/.env als GITHUB_TOKEN, oder frag Cody nach einem eigenen Token
mit "public_repo"-Scope.

Fuer wiederholtes Pushen ohne Passwort-Abfrage einmalig Credential Helper
setzen:

```bash
git config --global credential.helper store
```

Beim ersten Push landen die Zugangsdaten dann in ~/.git-credentials.

## Neue Fotos fuer ein Listing hinzufuegen

```bash
cd ebay-erna-images
mkdir -p listings/DEINE-SKU
cp /pfad/zu/foto1.jpg listings/DEINE-SKU/
cp /pfad/zu/foto2.jpg listings/DEINE-SKU/
git add listings/DEINE-SKU
git commit -m "Bilder fuer SKU DEINE-SKU"
git push
```

## Resultierende URL fuer eBay imageUrls

```
https://raw.githubusercontent.com/arosswog/ebay-erna-images/main/listings/DEINE-SKU/foto1.jpg
```

Diese URL kannst du direkt in eBay Inventory Item imageUrls eintragen -
sie ist dauerhaft, kein Ablauf nach 72h.

## Alternative: GitHub API statt Git (praktisch fuer execute_code)

Falls du lieber per Python/requests statt Git-Kommandos arbeitest, PUT
gegen die Contents API (Datei muss base64-kodiert werden):

```
PUT https://api.github.com/repos/arosswog/ebay-erna-images/contents/listings/<SKU>/<dateiname>.jpg
Header: Authorization: token <GITHUB_TOKEN>
Body: {"message": "Bild fuer <SKU>", "content": "<base64-Bilddaten>"}
```

Danach ist die Datei sofort unter der raw.githubusercontent.com-URL oben
abrufbar (kann 1-2 Minuten CDN-Cache brauchen).

## Wichtig

- Repo ist OEFFENTLICH (muss es sein, damit eBay/Kaeufer die Bilder sehen).
  Keine privaten/sensiblen Inhalte hier ablegen, nur Produktfotos.
- Groessere Bilder (>5-10 MB) vorher komprimieren - Git-Repos werden sonst
  unnoetig gross. JPEG-Qualitaet 85 reicht fuer eBay meist locker.
