# Aquiplicity-2026
Attempting to get the program to not only see pixel changes but also quantity for perspective characters

**Advanced Multi-Image Compositing Tool**  
*Max-Deviation Layer Selection • Single Threshold • Area Lasso & Brush Draw*

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Canvas](https://img.shields.io/badge/Canvas-FF6B6B?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![No Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen)](https://github.com)

A powerful, **zero-install**, browser-based application for intelligently compositing multiple photographs of the same subject into one master image. Built for photographers and digital artists who want precise control over which parts of each shot make it into the final result.

---

## ✨ Key Features

### Intelligent Auto-Composition
- **Max-Deviation Layer Selection** — The core algorithm automatically finds, for every pixel, the layer that deviates the **most** from the base image (first uploaded photo). Only applies the change if the deviation exceeds your chosen threshold.
- Single global **Threshold** slider (1%–100%) gives you intuitive control over how aggressively the tool pulls in variation from other shots.
- Layers are pre-smoothed (6 iterations) before deviation calculation for cleaner, more natural results.
- Tie-breaker logic slightly prefers later-uploaded layers when deviations are very close (great for intentional poses).

### Powerful Manual Refinement Tools
| Tool                  | How to Use              | What It Does |
|-----------------------|-------------------------|--------------|
| **Brush**             | Left-click + drag       | Brings forward pixels from the layer present at the **start** of your stroke. Brush size adjustable (4–200 px). |
| **Patch Lasso**       | `Ctrl` + drag           | Instantly replaces the entire lassoed area with pixels from the starting layer. |
| **Blend Lasso**       | `Alt` + drag            | Feathers/blends the selected region for soft, natural transitions. |
| **Gradient Lasso**    | `Shift` + drag          | Applies a smooth color gradient overlay inside the selection (great for creative effects or fixing lighting). |

- **Undo** support (button + `Ctrl`/`Cmd` + `Z`, up to 15 steps)
- Real-time visual feedback while drawing lassos and brushes

### Workflow Features
- **Auto-compose on load** — Upload 2+ images and the app immediately generates a master composite.
- **Thumbnail strip** on the left with one-click removal (× button) of unwanted layers.
- **Dark / Light mode** toggle for comfortable long editing sessions.
- **"By Tracy Rose" preset** — One-click sets threshold to ~13% (excellent starting point for most portrait work).
- Export final result as high-quality PNG (`Aquiplicity_Master_MaxDeviation.png`).

---

## 🚀 How to Use

### Quick Start (30 seconds)
1. Download `index.html` (or the single HTML file) and open it in any modern browser (Chrome, Edge, Firefox recommended).
2. Click **Choose Files** and select 3–12 images of your subject (ideally same framing, same lighting).
3. The app automatically composes them using the current threshold.
4. Adjust the **Threshold** slider and click **Compose!** to re-process.
5. Use the brush or lasso tools to perfect specific areas.
6. Click **Save Master Image** when done.

### Detailed Workflow

**Step 1: Upload**
- First image becomes the **base/reference** layer.
- All subsequent images are resized to match the first image’s dimensions.
- Thumbnails appear on the left sidebar.

**Step 2: Compose**
- Use the **Threshold** slider (default 15%).
- Lower values = more conservative (only very different pixels are pulled in).
- Higher values = more aggressive compositing.
- Click **Compose!** or use the Tracy Rose preset button.

**Step 3: Refine**
- **Brush tool**: Click and drag over eyes, mouth, hair, hands, etc. The brush samples whichever layer was active at the point where you started drawing.
- **Lasso tools**: Hold the modifier key while dragging to create a selection, then release. The action is applied immediately.

**Step 4: Iterate**
- Remove bad layers with the × on thumbnails.
- Undo any mistake.
- Re-compose after major changes if needed.

**Step 5: Export**
- Click **Save Master Image** — your final composite is downloaded as a lossless PNG.

---

## 🧠 How the Max-Deviation Algorithm Works

For every pixel in the output:

1. Smooth all layers using a simple 4-neighbor averaging filter (6 iterations).
2. Calculate the Euclidean color distance in RGB space between each smoothed layer and the **base layer** (layer 0).
3. Find the layer with the **maximum deviation**.
4. If that maximum deviation exceeds the threshold → use the **original** (unsmoothed) pixel from that layer.
5. Otherwise → keep the base layer’s pixel.
6. A small tie-breaker prefers higher layer indices when deviations are nearly identical.

This approach excels at bringing forward micro-expressions, eye direction, hair position, and other fleeting moments from a burst of shots while keeping the overall lighting and pose consistent with your base image.

---

## 📁 Project Structure

This is a **single-file application** — everything (HTML, CSS, JavaScript) is contained in one `.html` file. No build step, no dependencies, no server required.

```
Aquiplicity-2026/
├── index.html          # The complete application
├── README.md           # This file
└── (optional) examples/
```

---

## 💡 Tips for Best Results (Photography)

- Always upload your **best overall shot first** (it becomes the base).
- Shoot in bursts with consistent lighting and framing.
- Use the Tracy Rose 13% preset as your starting point for portraits.
- Combine automatic composition with targeted brush strokes for eyes and mouth — this is where the tool shines.
- The brush and patch tools respect the **current layer matrix**, so you can pull from any layer that was selected during composition.

---

## 🛠 Technical Details

- Pure vanilla JavaScript + HTML5 `<canvas>`
- Uses `ImageData` for direct pixel manipulation (very fast)
- Memory-conscious: processes one row at a time with progress reporting
- Supports images up to ~4000×4000 px (larger sizes work but may be slow)
- All processing happens 100% client-side — your photos never leave your computer

---

## 📜 License

This project is released under the **MIT License**. Feel free to use it personally or commercially, modify it, and share your improvements.

---

## 🙏 Credits & Inspiration

- Developed with ❤️ for photographers who love having ultimate control over their composites.
- The “By Tracy Rose” preset is named in honor of a talented photographer whose workflow inspired many of the default settings.
- Special thanks to everyone who has ever said “I wish I could just paint the best parts of each photo together.”

---

## 🤝 Contributing

Pull requests and feature suggestions are welcome! Some ideas for future versions:
- Multi-layer brush (choose specific source layer)
- Mask import/export
- Batch processing
- WebGL acceleration for very large images
- Mobile / touch support

---

**Made for creators who want the best of every shot — in one beautiful image.**

*Open `index.html` in your browser and start composing.*
