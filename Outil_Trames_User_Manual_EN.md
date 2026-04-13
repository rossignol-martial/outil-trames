# OUTIL TRAMES
## User Manual — Version 1.1

**Martial Rossignol**  
Original algorithm: Jean-Noël Lafargue  
License CC BY-NC-SA 4.0

---

## 1. Overview

Outil Trames is a web-based artistic halftone tool using directed line hatching. It converts a source image into a network of hatching lines whose density and direction reproduce the tonal values of the original. The result can be exported as a multi-layer SVG compatible with Inkscape, or as a PNG for direct use.

Designed for screen printing, engraving, risography and any printing technique where line-based halftoning is preferable to traditional dot screens.

> **How to use** — Outil Trames is a standalone HTML file that opens directly in a web browser (Chrome, Firefox, Edge). No installation required. Open in **full screen** (F11 on Windows/Linux, Cmd+Ctrl+F on Mac) — the interface is designed to occupy the full screen width and all four columns are only fully visible in full screen mode.

### Language selection

The **FR** and **EN** buttons appear at the bottom of the left column. The choice is automatically saved in the browser. Switching is instant and does not affect current parameters.

### Credits and License

Developed by **Martial Rossignol**. Line halftone algorithm based on the work of **Jean-Noël Lafargue**.

Distributed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license: free to use provided you credit the authors, no commercial use without permission, redistribute modifications under the same license.

### Interface — four columns

| Left Column | Image Column |
|---|---|
| Open / image info | Interactive crop (popup) |
| Output format (series, number, orientation) | Tone (brightness, contrast, gamma) |
| Layout (margin, frame, target area) | Levels (black/white input) |
| H and V position | Gray range |
| SVG / PNG export | Gaussian blur / Sharpness |
| Color/Mono — Language selector | |

| Central Column | Processing Column |
|---|---|
| Interactive preview | Halftone parameters |
| Scroll wheel zoom (cursor-centered) | Line width |
| Click-drag pan | Line wobble |
| Zoom indicator | JSON parameter save/load |
| Status bar | Generated layers list |

---

## 2. Recommended Workflow

> **Before you start — full screen required** — Open the file in your browser, switch to full screen (F11 / Cmd+Ctrl+F). No internet connection required.

### Step 1 — Load the image
- Click ⊕ **Open image** or drag and drop into the central area
- Accepted formats: PNG, JPG, GIF, WEBP
- The original image appears in the Image column for cropping

> **Tip** — Use a grayscale image when possible — results are more predictable.

### Step 2 — Crop (optional)
- Click **✂ Crop…** to open the full-screen popup
- Choose an aspect ratio: Free, Original, 1:1, 3:2, 2:3, 4:3, 3:4, 16:9
- Draw the selection diagonally — the ratio is automatically enforced
- Click **✓ Apply** — the preview updates immediately
- **↺ Full image** cancels the crop

### Step 3 — Image pre-processing

Work in this order:
1. **Levels** — adjust Black and White input to stretch the histogram
2. **Gamma** — correct midtones (> 1 lightens midtones)
3. **Gray range** — positive stretches the range, negative compresses it
4. **Highlight comp.** — recovers detail in overexposed areas
5. **Brightness / Contrast** — global adjustments, apply last
6. **Blur** — light Gaussian blur (1–2) for smoother transitions
7. **Sharpen** — accentuates edges for crisper lines

> **Critical order** — Always apply levels and gamma BEFORE brightness/contrast.

### Step 4 — Output format
- Select the series (A, B or C), number (0 to 6) and orientation
- Set the white margin and frame thickness
- Target area: choose if the drawing should occupy a reduced surface
- H / V position: place the drawing within the area

### Step 5 — Halftone parameters
- **Layers (1–12)**: number of superimposed hatching directions
- **Min/Max threshold**: tonal range processed
- **Min/Max spacing**: distance between lines (dark / light areas)
- **Start angle**: orientation of the first layer's hatching
- **Line width**: 0.8 default, suited for fine screen printing

> **Screen printing** — Width 0.8, min spacing 6, max spacing 20, 1–2 layers. Avoid angles near 0° or 90°.

### Step 6 — Line wobble (optional)
- **Line wobble** (0–5 px): perpendicular oscillation amplitude. Endpoints remain fixed.
- **Wobble freq.** (0.5–8): number of cycles along a line's length

> **Subtlety** — Amplitude 0.5–1.0, frequency 2: almost imperceptible in print, humanizes the halftone.

### Step 7 — Layer management
- Click the eye icon to show/hide a layer
- Hidden layers are preserved in the SVG export

### Step 8 — Export
- **↓ Export SVG**: multi-layer Inkscape SVG, coordinates in mm
- **↓ Export PNG**: preview capture (screen resolution)
- **↓ Params / ↑ Params**: save/load parameters as JSON

---

## 3. Parameter Reference

### Left Column — Format and Layout

| Parameter | Range | Description |
|---|---|---|
| Series | A, B, C | ISO series |
| Number | 0–6 | A0 (841×1189) to A6 (105×148 mm) — same logic for B and C |
| Orientation | Portrait / Landscape | |
| White margin | 0–50 mm | Space between paper edge and drawing |
| Frame width | 0–10 mm | Border around drawing (0 = no frame) |
| Target area | Full page, ½ width, ½ height, ISO format | Surface for the drawing |
| H / V position | Left/Center/Right — Top/Middle/Bottom | Placement within the area |

### Image Column — Pre-processing

| Parameter | Range | Description |
|---|---|---|
| Brightness | –100 / +100 | Global additive shift |
| Contrast | –100 / +100 | Amplification around mid-gray |
| Highlight comp. | 0 / 100 | Non-linear compression of highlights |
| Gamma | 0.1 / 3.0 | Power curve (1.0 = neutral) |
| Black input | 0 / 254 | Low levels threshold |
| White input | 1 / 255 | High levels threshold |
| Gray range | –100 / +100 | Stretches (+) or compresses (–) the tonal range |
| Blur | 0 / 10 | Gaussian blur sigma |
| Sharpen | 0 / 5 | Laplacian sharpening filter |

### Processing Column — Halftone

| Parameter | Range | Description |
|---|---|---|
| Layers | 1–12 | Number of hatching directions |
| Min threshold | 0.001–0.999 | Luminosity at which lines appear |
| Max threshold | 0.001–0.999 | Luminosity at which lines disappear |
| Min spacing | 2–100 px | Spacing in dark areas |
| Max spacing | 2–100 px | Spacing in light areas |
| Start angle | 0–180° | Direction of the first layer |
| Line width | 0.1–8 | Thickness in pixels (default 0.8) |
| Line wobble | 0–5 | Perpendicular oscillation amplitude |
| Wobble freq. | 0.5–8 | Oscillation cycles per line |

---

## 4. Tips and Best Practices

- Convert to grayscale before loading when possible
- Crop BEFORE adjusting halftone parameters
- Start with 2 layers, 45° angle, equal spacings of 15
- Wobble sliders do not retrigger the halftone calculation — instant response
- The default format (series, number, orientation) is automatically remembered
- Hidden layers are exported with `display="none"` in the SVG — recoverable in Inkscape

---

## 5. SVG Export Structure

- inkscape: and sodipodi: namespaces included
- `document-units="mm"` — Inkscape opens in millimeters
- **Background** layer: white rectangle
- **Halftone 1–N** layers: one group per direction with angle in degrees
- **Frame** layer: modifiable border
- Coordinates in mm to 4 decimal places

---

*Outil Trames v1.1 — © Martial Rossignol — CC BY-NC-SA 4.0*
