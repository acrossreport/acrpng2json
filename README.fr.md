🇬🇧 [English](README.md) | 🇯🇵 [日本語](README.ja.md)

# ACR PNG2JSON

Un outil qui analyse une image PNG numérisée d'un rapport papier et convertit ses lignes, formes, zones colorées, tableaux et texte (via OCR) en un format JSON pouvant être importé directement dans le Free Canvas d'[ACR (Across Report Renderer)](https://acrossreport.com).

Gratuit à utiliser et à redistribuer. Le code source n'est pas publié, mais l'exécution et la redistribution ne sont soumises à aucune restriction.

---

## Fonctionnalités

- Détection automatique des lignes, formes, zones colorées et tableaux dans une image PNG
- Lecture du texte par OCR, avec enregistrement de sa position en millimètres
- Conversion des pixels en millimètres précis, à partir d'un format de papier spécifié (A4/A3/B4/B5), de dimensions explicites (mm), ou du DPI réel du scan
- Le fichier JSON obtenu peut être importé directement dans ACR Free Canvas

À utiliser lorsque vous devez importer dans ACR un rapport qui n'existe qu'au format papier, afin de pouvoir l'éditer et le réimprimer.

---

## Plateforme prise en charge

Windows uniquement (x64).

---

## Téléchargement

Téléchargez le dernier `png_to_json.exe` depuis les [Releases](../../releases). Le fichier pèse environ 400 Mo, car il intègre l'ensemble du moteur OCR et ses modèles de langue. Aucune installation n'est nécessaire — il suffit de l'exécuter.

---

## Utilisation

```
png_to_json.exe entree.png [sortie.json]
```

Si le nom du fichier de sortie est omis, `result.json` est créé.

### Spécifier un format de papier

```
png_to_json.exe scan.png sortie.json --paper-size A4
```

Formats pris en charge : `A4` / `A3` / `B4` / `B5` (insensible à la casse)

### Spécifier des dimensions exactes (mm)

```
png_to_json.exe scan.png sortie.json --width-mm 210 --height-mm 297
```

### Spécifier le DPI du scan (le plus précis)

```
png_to_json.exe scan.png sortie.json --dpi 300
```

Lorsque `--dpi` est indiqué, la même échelle est utilisée sur les deux axes, ce qui élimine par conception tout risque de distorsion. Cette option est prioritaire sur `--paper-size` et `--width-mm`.

### Options

| Option | Description |
|--------|-------------|
| `image` | Fichier PNG d'entrée (obligatoire) |
| `output` | Fichier JSON de sortie (par défaut `result.json`) |
| `--paper-size` | Format de papier (A4/B4/B5/A3) |
| `--width-mm` / `--height-mm` | Dimensions explicites en millimètres |
| `--dpi` | DPI réel du scan. Priorité maximale ; conversion sans distorsion |
| `--no-ocr` | Ignore la reconnaissance de texte (OCR), pour un traitement plus rapide |

Au moins l'un des éléments suivants doit être spécifié : format de papier, dimensions ou DPI.

---

## Ouvrir le fichier JSON converti

Le fichier JSON obtenu peut être importé dans la fonctionnalité Free Canvas d'[ACR Designer](https://acrossreport.com). Une fois importé, il peut être édité, exporté en PDF et imprimé comme tout autre rapport.

---

## Support

Cet outil est fourni gratuitement, sans garantie ni obligation de support. Si vous avez besoin d'aide pour la migration (ajustement de la précision de reconnaissance, conversion en masse de nombreux scans, etc.), un support payant est disponible sur demande. Contact : across.support@gmail.com

---

## Licence

Copyright (C) 2026 Across Systems Corporation.

Exécution et redistribution libres. Décompilation et modification interdites. Voir le fichier LICENSE.txt fourni pour plus de détails.
