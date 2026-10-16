# A4 বাংলা Notice & Press Release Generator (Pro Editor) for Bangladesh Jatiotabadi Chatrodal Units

A single-file, browser-based Bengali letterhead & notice generator that fits perfectly on A4 paper — with rich text editing, signature blocks, watermark, and one-tap **PNG / PDF** export.

No build step, no backend, no dependencies to install. Just open the HTML file and start typing.

---

## ✨ Features

- **A4-perfect layout** — 210mm × 297mm page with configurable margins (8–25 mm).
- **Rich text editor** — bold, italic, underline, colour, font family, font size, line spacing, paragraph spacing, and alignment.
- **Smart selection-based formatting** — style only the text you select; the rest of the document is untouched.
- **Dynamic editor height** — the text area grows and shrinks with the content, so short notices leave room to move the signature block upward.
- **Three-column signature zone** — each column supports an uploaded signature image plus editable name / designation text.
- **Movable signature block** — drag the handle (or use the ▲ / ▼ nudge buttons) to place signatures anywhere on the page; double-click the handle to reset to the default position.
- **Logo & auto watermark** — the left logo is automatically used as a faint background watermark.
- **Auto-resizing reference / date fields** — the width of `সূত্র` and `তারিখ` inputs adapt to their content.
- **One-tap export**
  - **PDF** via the browser’s native print dialog (A4, no margins).
  - **PNG** via `html2canvas` at 3× scale.
- **Auto-save** — everything (text, logos, signatures, margins, signature offset) is stored in `localStorage`.
- **Mobile-first editing path** — a dedicated touch selection engine that keeps your selection alive while you tap the toolbar.
- **Fully offline-capable** — once the page and fonts have loaded, it works without a connection.

---

## 🚀 Quick Start

1. Download or clone the repository.
2. Open `jcd notice releases.html` (or rename it to `index.html`) in any modern browser.
3. Start typing.

That’s it. There is nothing to install or compile.

> **Tip:** To host it on GitHub Pages, rename the file to `index.html` and enable Pages in your repository settings.

---

## 📖 How to Use

### Toolbar reference

| Control | Description |
| --- | --- |
| **মার্জিন** | Left/right page margin (8, 10, 12, 14, 16, 20, 25 mm). |
| **Noto Serif / Noto Sans** | Font family for the selected text. |
| **10 – 36** | Font size in pixels for the selected text. |
| **1.0 – 2.5** | Line height for the selected paragraph(s). |
| **প্যারা 0 – 2.0** | Bottom margin (paragraph spacing) for the selected paragraph(s). |
| **B / I / U** | Bold / Italic / Underline. |
| **Alignment** | Left, center, right, justify. |
| **🎨 Colour picker** | Text colour. |
| **+ সিগনেচার** | Show / hide the signature section. |

### Letterhead header

- Click the **left logo** circle to upload an image — it also becomes the page watermark.
- Click the **right logo** square to upload a second image.
- `বাংলাদেশ জাতীয়তাবাদী ছাত্রদল`, the unit name, and the address are all editable in place.
- `সূত্র` and `তারিখ` inputs auto-size as you type.

### Body editor

- Click the placeholder text and start writing.
- Select any text, then use the toolbar to change font, size, spacing, colour, or alignment.
- The editor box **automatically adjusts its height** to the amount of content.

### Signature zone

- Toggle visibility with the **+ সিগনেচার** button in the toolbar.
- Upload a signature image by clicking the dashed box in each column.
- Edit the name and designation directly.
- **Move the whole block** by dragging the ⠿ handle, or use the ▲ / ▼ buttons for 5 mm steps.
- **Double-click** the handle to snap the block back to its default position (25 mm).

### Export

- **PDF সেভ** → opens the browser print dialog. Choose “Save as PDF” and set margins to *None*.
- **PNG সেভ** → downloads a high-resolution PNG of the full A4 page.

All editor chrome (toolbar, drag handle, placeholders) is automatically hidden during export.

---

## 📱 Mobile vs Desktop Editing

The app uses two different editing engines depending on the input device.

| | Desktop (fine pointer) | Mobile / Tablet (coarse pointer) |
| --- | --- | --- |
| **Selection** | Native browser selection | Snapshot into `savedRange`, visualised with the CSS Custom Highlight API |
| **Formatting** | `document.execCommand` | Direct DOM manipulation (`<span>` wrapping, block styles) |
| **Why** | Works perfectly with a mouse | `execCommand` loses the selection the moment the toolbar is tapped |

On mobile you will also see a **blue highlight** over the selected text so you always know what will be styled.

---

## 💾 Auto-save & Data

Everything is stored in `localStorage` under the key:

```js
a4LetterheadV24
