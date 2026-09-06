# ebay-erna-images

Oeffentliches Bild-Hosting fuer eBay-Listings (Rossi / Erna).

## Struktur

Bilder liegen unter `listings/<SKU>/<dateiname>.jpg`, z.B.:

```
listings/ART-12345/foto1.jpg
listings/ART-12345/foto2.jpg
```

## Dauerhafte Bild-URL fuer eBay (imageUrls)

Kein GitHub Pages noetig - raw.githubusercontent.com reicht fuer eBay
Inventory-Item imageUrls direkt aus:

```
https://raw.githubusercontent.com/arosswog/ebay-erna-images/main/listings/<SKU>/<dateiname>.jpg
```

Diese URL ist dauerhaft stabil, solange die Datei im main-Branch bleibt
(kein 72h-Ablauf wie bei litterbox.catbox.moe).

## Bilder hochladen

Siehe UPLOAD.md fuer die einfachste Methode (Git via Terminal oder GitHub API).
