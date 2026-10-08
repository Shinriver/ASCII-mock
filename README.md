# ASCII-mock

An interactive Three.js video-to-ASCII visualizer. The project turns a live HTML video texture into a configurable flower-like render, with ASCII, dots, round dots, and Bayer dither styles.

## Live demo

[Open BLOOM.SEQ](https://shinriver.github.io/ASCII-mock/)

## Features

- Live `THREE.VideoTexture` rendering from `outputs/flower.mp4`
- Render styles: `round-dots`, `ascii`, `dither`, and `dots`
- Processing modes: `enhanced` and `realtime`
- Background modes with chroma keying, matte preview, spill suppression, and clarity controls
- Optional blurred source-video layer beneath the render layer
- Reverse-loop playback for open-to-close motion
- Browser-side GIF and WebM export at fixed frame timing
- Resolution tuning from 48 to 600 columns, with 180 as the default
- Responsive light and dark interface themes

## Run locally

Serve the repository over HTTP so the video and module imports load correctly:

```bash
python3 -m http.server 8123
```

Then open [http://127.0.0.1:8123/](http://127.0.0.1:8123/).

The root `index.html` forwards to `outputs/index.html`, which is also the source editor file.

## Controls

Open `TUNE` to adjust processing, render style, background, resolution, keying, clarity, overlays, source video visibility, reverse loop, and export options. `FPS` shows the live frame rate.

## Project structure

```text
index.html            # GitHub Pages entry point
outputs/index.html    # editor application
outputs/flower.mp4    # default source video
```

## Notes

The editor is a static browser application and does not require a backend. WebM export depends on browser WebCodecs support; GIF export is available as a browser-side fallback.
