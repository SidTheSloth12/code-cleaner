# Code Cleaner

A lightweight, standalone HTML5 code cleanup utility with 4 aggressive levels of whitespace and comment removal.

## Features

- **4 cleanup levels:**
  - `readable` — removes blank lines and normalizes operator spacing, keeps comments and indentation
  - `compact` — strips comments and blank lines, preserves indentation for readability
  - `minified` — removes comments, blank lines, and indentation for maximum compaction
  - `nuclear` — collapses everything into a single dense line (unreadably small)

- **Smart language detection** — auto-detects JavaScript, Python, CSS, HTML, Java, C/C++, Rust, Go, Ruby, PHP, and Swift
- **Granular control** — toggle comments, indentation, blank line removal, and operator spacing independently
- **Live statistics** — see line/character count before and after, plus reduction percentage
- **Dark editor theme** — professional dark UI designed for long coding sessions
- **No dependencies** — pure HTML/CSS/JavaScript, runs offline in any browser

## How to Use

1. Download `code-cleaner.html`
2. Open in any modern browser
3. Paste your code into the input pane
4. Select a cleanup level or customize with toggles
5. Copy the cleaned output

## What It Does

- Removes excessive whitespace and blank lines
- Strips comments (with an option to keep them)
- Normalizes operator spacing (e.g., `a=b` → `a = b`)
- Optionally removes indentation for extreme size reduction
- Supports language-aware comment removal

## Use Cases

- **Code golfing** — extreme size reduction for competitions
- **Obfuscation** — make code harder to read (use responsibly!)
- **Optimization** — reduce file size for deployment
- **Cleanup** — remove messy formatting before processing
- **Learning** — understand whitespace handling across languages

## Technical Details

- Pure JavaScript — no build tools, no npm, no dependencies
- Single HTML file — copy and distribute freely
- Runs entirely in the browser — no data sent anywhere
- Tab key support in the input textarea
- Keyboard-friendly interface

## License

MIT — use freely, modify, distribute.
