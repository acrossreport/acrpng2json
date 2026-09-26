🇬🇧 [English](README.md) | 🇫🇷 [Français](README.fr.md)

# ACR PNG2JSON

紙の帳票をスキャンした PNG 画像を解析し、罫線・図形・色領域・表・文字(OCR)を [ACR (Across Report Renderer)](https://acrossreport.com) の Free Canvas にそのまま取り込める JSON 形式に変換するツールです。

無償・再配布自由です。ソースコードは非公開ですが、実行・配布に制限はありません。

---

## できること

- PNG 画像から、罫線・図形・色の塗られた領域・表・文字を自動検出
- 文字部分は OCR で読み取り、位置(mm 単位)とあわせて記録
- 用紙サイズ(A4/B3/B4/B5)または実寸(mm)、もしくは印刷 DPI を指定して、ピクセルを正確な mm に換算
- 出力した JSON は、そのまま ACR Free Canvas に取り込み可能

紙でしか残っていない既存の帳票を、ACR で編集・再印刷できる形に変換したいときに使います。

---

## 対応環境

Windows のみ(x64)。

---

## ダウンロード

[Releases](../../releases) から、最新版の `png_to_json.exe` をダウンロードしてください。ファイルサイズが約400MBあります。これは、文字認識(OCR)エンジンと、その言語モデルを内部にすべて含んでいるためです。インストール作業は不要で、そのまま実行できます。

---

## 使い方

```
png_to_json.exe 入力.png [出力.json]
```

出力先を省略すると、`result.json` という名前で作成されます。

### 用紙サイズを指定する場合

```
png_to_json.exe scan.png output.json --paper-size A4
```

対応する用紙サイズ: `A4` / `A3` / `B4` / `B5`(大文字・小文字どちらでも可)

### 実寸(mm)を指定する場合

```
png_to_json.exe scan.png output.json --width-mm 210 --height-mm 297
```

### スキャン時の DPI が分かっている場合(最も正確)

```
png_to_json.exe scan.png output.json --dpi 300
```

`--dpi` を指定すると、縦横で同じ倍率で mm に換算するため、画像の歪みが原理的に起きません。`--paper-size` や `--width-mm` より優先されます。

### オプション一覧

| オプション | 説明 |
|-----------|------|
| `image` | 入力 PNG ファイル(必須) |
| `output` | 出力 JSON ファイル(省略時は `result.json`) |
| `--paper-size` | 用紙サイズ(A4/B4/B5/A3) |
| `--width-mm` / `--height-mm` | 実寸(mm)を直接指定 |
| `--dpi` | スキャン時の実 DPI。指定時は最優先で、歪みなく換算 |
| `--no-ocr` | 文字認識(OCR)をスキップする(処理を高速化したいときに) |

用紙サイズ・実寸・DPI のいずれかは、必ず指定してください。

---

## 変換後の JSON を開くには

出力された JSON は、[ACR Designer](https://acrossreport.com) の Free Canvas 機能で取り込めます。取り込んだ後は、通常の帳票と同じように編集・PDF出力・印刷ができます。

---

## サポートについて

無償でご利用いただけますが、動作保証やサポートはございません。認識精度の調整や、大量のスキャン画像の一括変換など、移行作業でのご支援をご希望の場合は、個別にサポート契約を承っております。お問い合わせは across.support@gmail.com まで。

---

## ライセンス

Copyright (C) 2026 Across Systems Corporation.

本ツールの実行・配布は自由に行っていただけます。逆コンパイル・改変は禁止します。詳細は同梱の LICENSE.txt をご覧ください。
