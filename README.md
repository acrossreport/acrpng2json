🇯🇵 [日本語](README.ja.md) | 🇫🇷 [Français](README.fr.md)

# ACR PNG2JSON

A tool that analyzes a scanned PNG image of a paper-based report and converts its lines, shapes, colored regions, tables, and text (via OCR) into a JSON format that can be imported directly into [ACR (Across Report Renderer)](https://acrossreport.com) Free Canvas.

Free to use and redistribute. The source code is not published, but execution and redistribution are unrestricted.

---

## What it does

- Automatically detects lines, shapes, colored regions, and tables in a PNG image
- Reads text via OCR and records its position in millimeters
- Converts pixels to accurate millimeters using a specified paper size (A4/A3/B4/B5), explicit dimensions (mm), or the scan's actual DPI
- The resulting JSON can be imported directly into ACR Free Canvas

Use this when you need to bring an existing paper-only report into ACR, so it can be edited and reprinted.

---

## Supported platform

Windows only (x64).

---

## Download

Download the latest `png_to_json.exe` from [Releases](../../releases). The file is about 400MB, because it bundles the entire OCR engine and its language models. No installation is required — just run it.

---

## Usage

```
png_to_json.exe input.png [output.json]
```

If the output filename is omitted, `result.json` is created.

### Specifying a paper size

```
png_to_json.exe scan.png output.json --paper-size A4
```

Supported sizes: `A4` / `A3` / `B4` / `B5` (case-insensitive)

### Specifying exact dimensions (mm)

```
png_to_json.exe scan.png output.json --width-mm 210 --height-mm 297
```

### Specifying the scan's DPI (most accurate)

```
png_to_json.exe scan.png output.json --dpi 300
```

When `--dpi` is given, the same scale is used for both axes, so distortion cannot occur by design. This takes precedence over `--paper-size` and `--width-mm`.

### Options

| Option | Description |
|--------|-------------|
| `image` | Input PNG file (required) |
| `output` | Output JSON file (defaults to `result.json`) |
| `--paper-size` | Paper size (A4/B4/B5/A3) |
| `--width-mm` / `--height-mm` | Explicit dimensions in millimeters |
| `--dpi` | Actual DPI of the scan. Takes highest priority; converts without distortion |
| `--no-ocr` | Skip OCR text recognition (for faster processing) |

At least one of paper size, dimensions, or DPI must be specified.

---

## Opening the converted JSON

The resulting JSON can be imported into [ACR Designer](https://acrossreport.com)'s Free Canvas feature. Once imported, it can be edited, exported to PDF, and printed like any other report.

---

## Support

This tool is provided free of charge with no warranty or support obligation. If you need assistance with migration work (tuning recognition accuracy, bulk conversion of many scans, etc.), paid support is available on request. Contact: across.support@gmail.com

---

## License

Copyright (C) 2026 Across Systems Corporation.

Free to run and redistribute. Decompilation and modification are prohibited. See the included LICENSE.txt for details.
