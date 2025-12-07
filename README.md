# OBS HTML Text Slideshow

**Version 2.0** – A complete, standalone text slideshow system for OBS Studio. Control on-stream text slides with a modern browser dock, smooth transitions, and global hotkeys. Inspired by [Animated-Lower-Thirds](https://github.com/noeal-dac/Animated-Lower-Thirds), reimagined for text presentations.

![Dock Preview](https://i.imgur.com/dfnu3HP.png)

## 🚀 Quick Start (Super Easy Install)

### Installation from Release ZIP (Recommended)

1. **Download the latest release**:
   - Go to [Releases](https://github.com/ASchneiderBR/htmlTextSlideshow/releases)
   - Download `htmlTextSlideshow-X.Y.Z.zip` (latest version)
   
2. **Extract the ZIP file**:
   - Extract all files to a folder on your computer (e.g., `Documents\HTML-Text-Slideshow`)
   - **Important**: Extract directly - the ZIP contains files in the root (no subfolder)
   - You should see: `Dock.html`, `Source.html`, `text-slides.lua`, `README.md`, `LICENSE`

3. **Load the script in OBS**:
   - In OBS, go to **Tools → Scripts**
   - Click the `+` button
   - Browse and load **`text-slides.lua`** from the extracted folder

4. **Get file paths from Script Properties**:
   - In the **Script Properties** panel, you'll see two file paths:
     - **Dock URL** – Copy this path (starts with `file:///`)
     - **Source Path** – Copy this path

5. **Add the Dock**:
   - Go to `View > Docks > Custom Browser Docks...`
   - Click `+` to add a new dock
   - **Dock Name**: `Text Slides` (or any name you like)
   - **URL**: Paste the **Dock URL** from step 4
   - Click **OK**

6. **Add the Source to your scene**:
   - Add a **Browser Source** to your scene
   - Check **"Local file"**
   - Browse to select **`Source.html`**, or paste the **Source Path** into the URL field
   - Set width/height to match your canvas (e.g., 1920x1080)
   - Click **OK**

7. **Configure Hotkeys** (optional):
   - Go to `Settings > Hotkeys`
   - Search for "Text Slides"
   - Bind keys for:
     - **Text Slides: Next** – Advance to next slide
     - **Text Slides: Previous** – Go back to previous slide
     - **Text Slides: First** – Jump to first slide

8. **Done!** 
   - Open the **Text Slides** dock
   - Type or paste your content
   - Use `---` on a blank line to separate slides
   - Click **"Add slides"** to publish
   - Control slides with the dock buttons or your hotkeys during streaming!

## 📁 Files (All-In-One Design)

Version 2.0 simplifies everything into just **3 core files** (plus auto-generated files):

**Core Files** (included in release ZIP):
- **`text-slides.lua`** – The installer script. Manages hotkeys and displays file paths.
- **`Dock.html`** – The control panel (standalone, all CSS/JS bundled inside).
- **`Source.html`** – The overlay display (standalone, all CSS/JS bundled inside).

**Auto-generated Files** (created automatically when you use the slideshow):
- **`hotkeys.js`** – Bridges Lua hotkey commands to the Dock (created by the Lua script).
- **`slides.json`** – Fallback storage for slides if BroadcastChannel fails (created automatically).

**Note**: The release ZIP contains only the core files. Auto-generated files are created in the same folder when you first use the slideshow.

## ✨ Features

### Typography & Styling
- **Markdown support:**
  - **Bold** (`**text**` or `__text__`), *Italic* (`*text*` or `_text_`), ~~Strikethrough~~ (`~~text~~`)
  - Headings (`# H1` through `###### H6`)
  - Lists: unordered (`- item`) and ordered (`1. item`)
  - Code blocks (` ```code``` `), inline code (`` `code` ``), blockquotes (`> quote`)
  - Links (`[text](url)`), images (`![alt](url)`)
- **Font control:**
  - 30+ fonts: Google Fonts (Montserrat, Roboto, Open Sans, Poppins, etc.) and System fonts
  - Custom font size (18px - 120px, respects line breaks)
- **Advanced text effects:**
  - **Color picker** with transparency control (applies to entire layer for consistent look)
  - **Shadow intensity** (0-100): from subtle to dramatic black shadow with increasing blur
  - **Stroke (outline)** intensity (0-10): adjustable text outline that renders behind characters
- **Alignment:**
  - Horizontal: Left, Center, Right
  - Vertical: Top, Middle, Bottom

### Slide Management
- **Slide transitions:**
  - 13 transition types: Crossfade, Fade, Slide (Left/Right/Up/Down), Zoom (In/Out), Push (Left/Right/Up/Down), None (instant)
  - Adjustable duration (0-2000ms)
  - **Smart transitions**: Only animates when changing slides or previewing transitions, not when editing formatting
- **Preview panel:**
  - Live markdown rendering
  - Drag-and-drop reordering
  - One-click slide activation
  - Active slide highlighting
- **Loop mode:** Auto-return to first slide after the last one
- **Persistent state:** All slides saved to browser localStorage and synced instantly

### OBS Integration
- **Global hotkeys:** Next, Previous, First Slide (bind in OBS Settings > Hotkeys)
- **Real-time sync:** Changes appear instantly via BroadcastChannel API
- **Fallback mode:** JSON polling if BroadcastChannel is unavailable
- **Zero dependencies:** No installation, no npm, no build process

## 🎬 Everyday Workflow

1. **Edit slides:** Type or paste text in the Dock. Use `---` on a blank line to separate slides.
2. **Style it:** Adjust font, color, shadow, stroke, and alignment in real-time.
3. **Publish:** Click **"Add slides"** to add them to your show.
4. **Present:** Click **Play** buttons in the preview, or use **Hotkeys** during your stream.

## 🔧 Technical Details

### Architecture (v2.0)
- **Standalone HTML files**: All CSS and JavaScript bundled inline—no external dependencies.
- **ES5 compatibility**: Pure JavaScript (no modules) for maximum OBS CEF browser compatibility.
- **BroadcastChannel sync**: Real-time communication between Dock and Source within the same OBS instance.
- **localStorage persistence**: Slides saved per OBS profile, survives restarts.
- **Lua bridge**: Hotkey commands written to `hotkeys.js`, polled by the Dock every second.

### What's New in v2.0
- **Simplified structure**: From 15+ files to just 3 core files (Dock.html, Source.html, text-slides.lua).
- **No build process**: Everything works directly from source—open the HTML in any browser.
- **Better installation**: Script properties display exact file paths with `file:///` prefix for easy copy/paste.
- **Enhanced typography**: Shadow and stroke effects, unified opacity control, better font rendering.
- **Improved performance**: Debounced inputs, markdown caching, optimized animations with GPU acceleration.

### Browser Compatibility
- **OBS Studio 28+** (Chromium Embedded Framework)
- **Any modern browser** (for testing the Dock outside OBS)

## 🤖 About the Development

**Disclaimer:** This project was created entirely using **AI-assisted coding tools (LLMs via Cursor)**.

- **100% AI-Generated**: Every line of code (v1.0 and v2.0) was generated by AI.
- **Human-Guided**: Direction, testing, and refinement by a human with zero coding knowledge.
- **Function over Form**: The priority was creating a robust, user-friendly tool.
- **Community Driven**: Pull Requests, bug reports, and feature requests are welcome!

## 💡 Use Cases

- **Live streaming**: Display talking points, quotes, lyrics, or audience questions.
- **Presentations**: Professional slide transitions without leaving OBS.
- **Church services**: Scripture verses, song lyrics, announcements.
- **Education**: Lecture notes, formulas, code snippets (with syntax highlighting via markdown).
- **Gaming**: Quest objectives, story text, patch notes.

## 📝 License

This project is licensed under the **GNU General Public License v2.0 or later** (GPL v2.0+), which is compatible with OBS Studio's license requirements.

This means:
- ✅ Free to use, modify, and distribute
- ✅ Source code must remain open and available
- ✅ Derivative works must also be licensed under GPL v2.0+

For the full license text, see the [LICENSE](LICENSE) file in this repository.

## 🙏 Credits

- Inspired by [Animated-Lower-Thirds](https://github.com/noeal-dac/Animated-Lower-Thirds) by noeal-dac.
- Developed with [Cursor](https://cursor.sh) AI assistance.
