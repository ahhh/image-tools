# image-tools

Browser-based image tooling. First tool: **Spritebench**, a single-file sprite / pixel-art editor.

## Spritebench — single-file browser sprite editor

Everything lives in [`sprite-editor.html`](sprite-editor.html) — no build step, no dependencies, works offline. Open it in any modern browser.

Derived from `Browser_Sprite_Editor_Plan.md` (single-file browser sprite/image editor: architecture, layers, tools, sprite/animation features, export).

### Feature roadmap

- [x] **1. App shell & canvas viewport** — dark workbench layout (tool rail, canvas, side panel, timeline), checkerboard transparency, zoom at cursor (wheel / `+` `-`), pan (space-drag / middle mouse), pixel grid toggle, crisp integer scaling
- [x] **2. Drawing tools** — pencil, eraser, eyedropper, flood fill, line, rectangle, ellipse (outline/filled), adjustable brush size, right-click draws with secondary color, shift-constrain for shapes
- [x] **3. Color system** — primary/secondary colors with swap, hex input, native picker, palette swatch grid (Sweetie-16 default), add current color / right-click to remove
- [x] **4. Undo / redo** — history stack for strokes and structural ops (layers, frames, resize), `Ctrl+Z` / `Ctrl+Shift+Z` / `Ctrl+Y`, capped depth
- [x] **5. Layers** — add / duplicate / delete / reorder, visibility toggle, per-layer opacity, merge down, rename (double-click), scale a layer's content independently of canvas size (nearest-neighbor, aspect lock, centered in place)
- [x] **6. Selection & clipboard** — rectangular select with marching ants, move/lift floating pixels, delete, select all / deselect, copy & paste as floating selection
- [x] **7. Animation** — frame timeline with live thumbnails, add / duplicate / delete / reorder frames, playback with FPS control, onion skinning
- [x] **8. Import / export** — export PNG at 1–16× scale, export horizontal spritesheet strip; **Open** loads a project (.json) or an image as a new document; **Import** places an image onto the selected layer as a floating selection (drag to position, other layers untouched)
- [x] **9. Canvas operations** — new document dialog with presets, resize canvas, flip horizontal/vertical, rotate 90°
- [x] **10. Shortcuts & polish** — full keyboard map (tool keys, `X` swap, `[` `]` brush size, `Delete`), status bar (cursor position, document size, zoom), tooltips

All ten features are implemented and verified end-to-end in headless Chromium (30/30 checks: draw/undo/fill/shapes, layer merge, selection move, copy/paste, frame playback, flip/rotate/resize, export, project round-trip).

### Controls

| Action | Input |
| --- | --- |
| Tools | `B` pencil · `E` eraser · `I` eyedropper · `F` fill · `L` line · `R` rect · `O` ellipse · `M` select · `V` move |
| Draw | left = primary, right = secondary, `Alt`+click = pick color, `Shift` = constrain shape |
| Brush size | `[` / `]` or the Tool panel slider |
| Colors | `X` swap, click a chip to open the picker, right-click a swatch to remove it |
| View | wheel = zoom at cursor, `Space`-drag or middle-drag = pan, `0` = fit, `G` = grid |
| History | `Ctrl+Z` undo, `Ctrl+Shift+Z` / `Ctrl+Y` redo |
| Selection | `Ctrl+A` all, `Ctrl+D` / `Esc` deselect, `Delete` clear, `Ctrl+C/X/V` copy/cut/paste |
| Animation | `Enter` play/pause, `,` / `.` previous/next frame |
| File | `Ctrl+S` save project, `Ctrl+Alt+N` new document |

On macOS use `Cmd` in place of `Ctrl`.
