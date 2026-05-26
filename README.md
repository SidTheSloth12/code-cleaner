# Code Cleaner

A lightweight, zero-dependency, single-file web utility designed to format, clean, and compress source code. Built entirely with native web technologies, it runs entirely client-side in the browser to ensure data privacy and instant processing.

---

## Features

* **Automatic Language Detection:** An internal regex scoring mechanism identifies the programming language of pasted code to apply the correct formatting rules.
* **Context-Aware Processing:** Tailors comment stripping and spacing adjustments to the specific syntax of the language detected.
* **Syntax Integrity Guardrails:** Displays real-time warnings if a selected cleaning level risks breaking the syntax of indentation-sensitive or newline-sensitive languages.
* **100% Client-Side:** Processes everything locally in your browser. No external API calls, tracking, or data transmission.
* **Dual-Pane Interface:** Shows live comparison metrics, including line counts, character counts, and the total percentage of file-size reduction.

---

## Cleanup Levels

The tool provides four preset processing levels to choose from:

| Level | Preset | Behavior |
| --- | --- | --- |
| **Level 0** | `readable` | Removes blank lines and normalizes operator spacing. Keeps all comments and indentation intact. |
| **Level 1** | `compact` | Strips comments and blank lines. Normalizes spacing and preserves indentation. |
| **Level 2** | `minified` | Removes comments, blank lines, and indentation entirely, but keeps code on multiple lines. |
| **Level 3** | `nuclear` | Compresses the code as much as possible, stripping all comments, blank lines, indentation, and unnecessary line breaks to output a single line. |

> **Custom Toggles:** You can override presets at any time by manually checking or unchecking individual rules for **comments**, **indentation**, **blank lines**, and **fixing spacing**.

---

## Technical Implementation

### 1. Heuristic Language Detection

The script tests input code against syntax patterns for 20 distinct formats (including JavaScript, TypeScript, Python, Rust, Go, SQL, HTML, CSS, and YAML):

* Identifies TypeScript via explicit types (`string`, `void`, `any`, `never`) and declarations (`interface`, `type ... =`).
* Detects Python using colons at line ends (`:$`), standard indentation definitions, and keywords (`def`, `elif`, `lambda`).
* Flags Shell scripts by scanning for shebang pathways (`#!/bin/bash`) on the first line.

### 2. Language-Specific Comment Stripping

Instead of a universal find-and-replace, the tool uses targeted regular expressions based on the language context:

* **Hash Comments (`#`):** Applied to Python, Ruby, YAML, and Shell (while preserving shebang lines).
* **C-Style Comments (`//` and `/* */`):** Used for JS, TS, Java, Kotlin, C/C++, Rust, Go, Swift, Dart, and Scala.
* **Custom Syntax:** Safely targets markup comments (``) for HTML, double-dashes (`--`) for SQL/Lua, and handles multi-style comments for PHP.

### 3. Syntax-Safe Spacing Normalization

The operator spacing engine cleans up code layouts without breaking language-specific tokens:

* **Bypass Matrix:** Completely skips operator modifications for `html`, `css`, `yaml`, `json`, `sql`, `sh`, and `lua` to preserve string layouts and configurations.
* **Token Protection:** Prevents formatting from breaking critical syntax symbols such as arrow functions (`->`, `=>`), scope resolutions (`::`), mutable references (`&mut`), assignment operators (`:=`), and stream operators (`<<`, `>>`).

---

## Integrity Warnings

To avoid breaking execution logic, the UI displays real-time warning banners under specific conditions:

* **Indentation Warning:** Triggered if you attempt to remove indentation from whitespace-dependent languages like `python`, `yaml`, `sh`, or `makefile`.
* **Newline Warning:** Triggered if you use the `nuclear` level to collapse code onto a single line for formats that rely on newlines to terminate statements (e.g., `python`, `yaml`, `sh`, `makefile`, `sql`).

---

## Getting Started

The entire application is self-contained within a single static HTML file. There are no dependencies, node modules, or build steps required.

### Running Locally

1. Clone the repository:
```bash
git clone https://github.com/SidTheSloth12/code-cleaner.git

```


2. Navigate into the directory and open the file directly in any modern web browser:
```bash
cd code-cleaner
open code_cleaner_tool.html

```



### Deployment

Because it is a static page, it can be hosted for free on **GitHub Pages**, **Vercel**, or **Netlify** by serving `code_cleaner_tool.html` as the entry index file.

---

## Project Details

* **Markup:** Semantic HTML5 layout.
* **Styling:** CSS3 custom properties with a custom dark-mode color scheme.
* **Fonts:** Uses `JetBrains Mono` for code blocks and `Syne` for titles via Google Fonts.
* **Core Logic:** Pure Vanilla JavaScript (ES6+) text processing.

