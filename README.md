# Clipping — Stickman Studio Pro

**Clipping** is a browser-based 9:16 vertical video creation studio for automatically turning voiceovers and ordered image scenes into a synchronized, captioned stickman-style video project.

The application is a single-page HTML/JavaScript experience that runs entirely in the browser. It uses image scenes, an uploaded voiceover, optional background music, script or AI-generated timing data, and canvas rendering to provide a live preview and MP4 export workflow.

> Repository description: “it sused to edit videos automatically”

## Live Preview

Open `index.html` directly in a modern desktop browser or serve the repository with a local static server. The interface provides a three-column studio workspace:

- scene and script controls
- a vertical 9:16 canvas preview
- scene-cut and caption controls

## Features

### Scene Management

- Upload multiple scene images at once or choose them one at a time.
- Drag and drop images into the scene area.
- Sort uploaded scenes by filename, modification time, or browser order.
- Use **Smart Auto** ordering to reduce operating-system upload scrambling.
- Rearrange scenes visually with **1→N Tap Order** or the scene gallery grid.
- Preview and jump between scenes from the timeline.

### Voiceover and Audio

- Upload MP3, WAV, or another browser-supported audio format as the voiceover.
- Add and remove optional background music.
- Adjust voiceover and BGM volume independently.
- Mute or unmute playback.
- Support pitch-preserving playback and playback-rate controls.
- Keep projects refresh-proof through browser IndexedDB storage.

### Automatic and Manual Sync

- Generate AI-assisted captions and timing with the **AI Transcribe & Sync** workflow.
- Use **Instant Pause Sync** for timing based on voice pauses.
- Paste scripts in scene blocks, paragraphs, one-line-per-scene, timestamped, SRT, or table formats.
- Automatically divide scripts into scenes or choose a specific split mode.
- Fine-tune image, caption, and global synchronization offsets.
- Evenly pace cuts against detected sentences.
- Reset cuts or apply manual scene changes while previewing.

### Captions

- Yellow highlight-pill captions.
- Bold white-outline captions.
- Minimal dark glass captions.
- Option to turn captions off.
- Adjustable vertical caption position.
- Live caption count and synchronized word highlighting.

### Visual Effects

- Smart mix of glide, focal zoom, and fade transitions.
- Glide push, focal zoom, silky fade, or hard-cut transitions.
- Natural, snappy, or cinematic breath-pause cut behavior.
- Performance tiers for automatic, high, balanced, or lite rendering.

### Preview and Export

- Live 9:16 canvas preview.
- Timeline scrubber and proportional scene timeline.
- Skip backward and forward controls.
- Live keyboard cut support: press **C** while playing to cut to the next scene.
- Export at 1080p, 720p, or 540p.
- MP4 export workflow with progress and cancel controls.
- Responsive dark interface with a graphite and violet visual system.

## Project Structure

```text
clipping/
└── index.html    # Complete application UI, styling, state, and browser-side logic
```

The repository currently contains one main file. `index.html` is a standalone web application with:

- Tailwind CSS loaded from a CDN
- Google Fonts for Inter and JetBrains Mono
- HTML5 Canvas rendering
- HTML Audio APIs
- IndexedDB local persistence
- Browser Media APIs for recording and export
- Optional in-browser transcription workers or AI pipelines

## Technology Stack

- HTML5
- CSS and Tailwind CSS
- JavaScript ES modules
- Canvas 2D API
- Web Audio / HTML Audio
- IndexedDB
- Media Recorder and browser media APIs
- Browser-native timing and animation APIs

No Node.js build step or package installation is required for basic use.

## Getting Started

### Option 1: Open the page directly

1. Clone the repository:

   ```bash
   git clone https://github.com/kernel-ux/clipping.git
   cd clipping
   ```

2. Open `index.html` in a modern browser.

Some browser features, particularly audio playback, transcription workers, file APIs, and export behavior, work more reliably when the project is served over HTTP rather than opened as a local file.

### Option 2: Use a local static server

With Python:

```bash
cd clipping
python3 -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

Other static-server options include VS Code Live Server, `npx serve`, or any HTTP server you prefer.

## How to Use

1. Open the application.
2. Upload a voiceover in the **Voiceover Audio** panel.
3. Optionally upload background music.
4. Upload one or more scene images.
5. Arrange scenes using the recommended upload order or the visual grid.
6. Paste or edit a script in the **Script** tab.
7. Click **AI Transcribe & Sync** or use **Instant Pause Sync**.
8. Adjust scene transitions and caption appearance under **Style & FX**.
9. Fine-tune image, caption, and global synchronization in the right panel.
10. Play the timeline and use **Cut Next** or the **C** keyboard shortcut when needed.
11. Choose an export quality and click **Export MP4**.

## Script Formats

The script editor accepts multiple formats, including:

```text
Scene 1 (0:00 - 0:04)
The first scene narration.

Scene 2 (0:04 - 0:08)
The second scene narration.
```

It also accepts:

- Blank-line-separated paragraphs
- One line per scene
- SRT-style timestamp blocks
- Timestamped tables
- Plain multiline text

The split mode can be changed to **Scene Blocks**, **One Line**, **Balanced Sentences**, or automatic smart splitting.

## Browser Requirements

Use a current version of:

- Google Chrome
- Microsoft Edge
- Firefox
- Safari

For the best experience:

- Enable JavaScript.
- Allow local file and media access.
- Use a desktop browser for full editing and export controls.
- Keep enough disk and memory available for long videos and high-resolution exports.
- Grant no special server permissions if browser APIs can already use local files.

## Local Storage and Privacy

The project stores project and media data in IndexedDB and aims to keep media local to the browser. Uploaded files are not intentionally sent to a repository server by this application. AI transcription or CDN-backed resources may depend on external browser requests when enabled or loaded.

## Export Notes

- Export quality options are 1080p, 720p, and 540p; **Auto** chooses the best available exported resolution.
- Export dimensions use portrait 9:16 ratios.
- Long videos, high-resolution images, and 1080p export require additional memory and processing time.
- Browser support for codecs and recording varies by platform.
- If an export is cancelled or unsupported, try a smaller export quality or a different browser.

## Development

This project intentionally uses a single-file architecture, so development is straightforward:

1. Edit `index.html`.
2. Refresh the browser.
3. Test scene upload, voiceover playback, synchronization, and export.
4. Exercise both desktop and narrow responsive layouts.

Before submitting a change, test at least:

- Multiple scene image formats
- Voiceover upload and playback
- Optional BGM playback
- Script parsing modes
- Playback and timeline seeking
- 9:16 canvas rendering
- Caption styles and offsets
- Export at the lowest and highest available quality

## Known Considerations

- Transcription quality depends on browser support and the selected synchronization model.
- Media export behavior varies by browser and installed codecs.
- Large image and audio files may use substantial memory.
- The project has no build pipeline or server-side backend.
- A network connection may be required for CDN-hosted Tailwind CSS and Google Fonts.
- Offline use may require bundling these dependencies and ensuring browser capabilities are available locally.

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make focused changes.
4. Test the application in a browser.
5. Open a pull request with reproduction and testing details.

Please keep changes responsive, accessible, and compatible with browser-only deployment.

### Contributors

- **Nirmal**
- [kernel-ux](https://github.com/kernel-ux)

## License

No license has been declared for this repository. Add an appropriate `LICENSE` file before using the project for commercial distribution or accepting third-party contributions.

## Repository

- [kernel-ux/clipping](https://github.com/kernel-ux/clipping)
- [Project page](https://github.com/kernel-ux/clipping)
