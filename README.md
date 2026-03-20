# 📺 TV Display Calibration Tool

A single-file, browser-based visual calibration tool for TVs and monitors connected via HDMI or DVI→HDMI. No installation, no dependencies — just open the HTML file in your browser and go fullscreen.

## Features

- **7-step guided calibration**: RGB range check → Brightness → Contrast → Gamma/Grayscale → Color & Saturation → Sharpness & Overscan → Reference image
- **Works in any modern browser** — no software to install, no USB stick needed
- **Single HTML file** — fully self-contained, runs offline
- **EN/DE language toggle** — switch between English and German in the UI
- **Keyboard navigation** — arrow keys to switch patterns, H for help overlay, ESC to return
- **Canvas-rendered test patterns** — pixel-accurate at 1920×1080

## Screenshots

Open `tv-calibration.html` → press F11 for fullscreen → click any step to start.

## Quick Start

1. Connect your PC to the TV via HDMI (or DVI→HDMI)
2. Set your PC's display output to **1920×1080**
3. Open `tv-calibration.html` in your browser
4. Press **F11** for fullscreen
5. Start with **Step 0 (RGB Range Check)** — this is critical!
6. Follow steps 1–6 in order

## RGB Range: The Most Common Pitfall

Most TVs interpret HDMI signals as **Limited Range (16-235)**, meaning:
- RGB 0–15 → all mapped to black
- RGB 236–255 → all mapped to white

If your GPU outputs **Full Range (0-255)** but the TV expects Limited Range, you'll lose detail in shadows and highlights. Step 0 detects this mismatch.

### How to fix it

**Option A** (preferred): Set the TV's HDMI input to "Full Range" or "PC Mode" (if your TV supports it).

**Option B**: Set your GPU to output Limited Range:

| GPU | Where to change |
|-----|----------------|
| **NVIDIA** | Control Panel → Display → Change Resolution → Output Dynamic Range → **Limited** |
| **AMD** | Radeon Settings → Display → Pixel Format / Color Range → **Limited / Studio** |
| **Intel** | Graphics Command Center → Display → Quantization Range → **Limited** |

After changing, re-run Step 0 to verify.

## What each step does

| Step | What it tests | What to adjust on TV |
|------|--------------|---------------------|
| 0 | RGB range match between GPU and TV | GPU driver or TV HDMI settings |
| 1 | Black level / shadow detail | **Brightness** |
| 2 | White level / highlight detail | **Contrast** |
| 3 | Gamma curve / grayscale neutrality | **Gamma** (if available); check for color tint |
| 4 | Color accuracy & saturation | **Color/Saturation**, **Color Temperature** |
| 5 | Sharpness artifacts & overscan | **Sharpness**, **Picture Format** (Just Scan / 1:1) |
| 6 | Overall visual impression | Final check — no adjustment needed |

## Recommended calibration order

1. RGB Range Check (Step 0) — fix this first, everything else depends on it
2. Brightness (Step 1) — set black level
3. Contrast (Step 2) — set white level
4. Gamma (Step 3) — verify grayscale
5. Color (Step 4) — adjust saturation and color temperature
6. Sharpness (Step 5) — minimize artifacts, disable overscan
7. Reference (Step 6) — verify with synthetic scene

## Compatibility

This tool works with any TV or monitor that accepts a 1080p signal via HDMI. It is designed for **visual calibration** (adjusting TV menu settings by eye), not for instrument-based color profiling.

### Tested on

| TV | Connection | GPU | RGB Range | Notes |
|----|-----------|-----|-----------|-------|
| Grundig 32 GFB 6822 (G7 chassis) | DVI→HDMI | NVIDIA (Limited) | Limited Range via GPU driver | TV has no Full Range option; works perfectly with GPU set to Limited |

> **Add your own!** If you've tested this tool on your TV, feel free to open a PR or issue with your setup details.

## Tips

- **DVI→HDMI**: DVI always outputs RGB. Audio is not transmitted. The signal is otherwise identical to HDMI.
- **PC as signal source**: If you only use HDMI from a PC (no cable/satellite box), set your TV's sharpness to **0** — the digital signal is already pixel-perfect, and any sharpening adds artifacts.
- **Color temperature**: "Warm" is usually closest to the D65 standard (6500K), but some TVs go overboard. Use whatever looks neutral on the gray patches in Step 3.
- **Overscan**: For PC use, always disable overscan (picture format "Just Scan", "Original", "1:1", or "Dot by Dot" — the name varies by manufacturer).

## License

This project is released into the public domain under [The Unlicense](https://unlicense.org/).

Do whatever you want with it. No attribution required.

---

---

# 📺 TV Display-Kalibrierungstool (Deutsch)

Ein browserbasiertes Kalibrierungstool für Fernseher und Monitore, die per HDMI oder DVI→HDMI angeschlossen sind. Keine Installation, keine Abhängigkeiten — einfach die HTML-Datei im Browser öffnen und Vollbild schalten.

## Funktionen

- **7-Schritte-Kalibrierung**: Farbraum-Check → Helligkeit → Kontrast → Gamma → Farbe & Sättigung → Schärfe & Overscan → Referenzbild
- **Läuft in jedem modernen Browser** — kein USB-Stick, keine Software nötig
- **Eine einzige HTML-Datei** — komplett eigenständig, läuft offline
- **EN/DE Sprachumschalter** — direkt im Tool umschaltbar
- **Tastatursteuerung** — Pfeiltasten, H für Hilfe, ESC zurück

## Schnellstart

1. PC per HDMI (oder DVI→HDMI) an den TV anschließen
2. PC-Ausgabe auf **1920×1080** stellen
3. `tv-calibration.html` im Browser öffnen
4. **F11** für Vollbild
5. Mit **Schritt 0 (Farbraum-Check)** starten — das ist entscheidend!
6. Schritte 1–6 der Reihe nach durchgehen

## RGB-Bereich: Die häufigste Fehlerquelle

Die meisten TVs interpretieren HDMI-Signale als **Limited Range (16-235)**. Wenn die GPU aber **Full Range (0-255)** ausgibt, gehen Details in dunklen und hellen Bereichen verloren. Schritt 0 erkennt dieses Problem.

### Lösung

**Option A** (bevorzugt): Am TV den HDMI-Eingang auf „Full Range" oder „PC-Modus" stellen (falls vorhanden).

**Option B**: GPU-Ausgabe auf Limited Range umstellen:

| GPU | Einstellung |
|-----|------------|
| **NVIDIA** | Systemsteuerung → Anzeige → Auflösung ändern → Dynamikbereich → **Begrenzt** |
| **AMD** | Radeon Einstellungen → Anzeige → Pixelformat / Farbbereich → **Begrenzt / Studio** |
| **Intel** | Grafikbefehlszentrale → Anzeige → Quantisierungsbereich → **Begrenzt** |

## Getestet mit

| TV | Verbindung | GPU | RGB-Bereich | Hinweise |
|----|-----------|-----|-------------|----------|
| Grundig 32 GFB 6822 (G7-Chassis) | DVI→HDMI | NVIDIA (Limited) | Limited Range über GPU-Treiber | TV hat keine Full-Range-Option; funktioniert mit GPU auf Limited einwandfrei |

> **Eigene Erfahrungen?** Gerne per PR oder Issue hinzufügen!

## Lizenz

Dieses Projekt ist gemeinfrei unter [The Unlicense](https://unlicense.org/).

Mach damit was du willst. Keine Namensnennung erforderlich.
