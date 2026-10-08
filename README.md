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

Open `TUNE` to adjust the editor:

### View

- **Processing** — choose `enhanced` for additional structure and clarity processing, or `realtime` for a lighter live-render path.
- **Render style** — choose `round-dots`, `ascii`, `dither`, or `dots`.

### Background

- **Background** — choose `black-background`, `white-background`, `green-screen`, `color-key`, or `off`.
- **Background color** — set the flat compositing color. Light backgrounds automatically switch the interface to a light theme.

### Clarity

- **Resolution** — controls the render grid from 48 to 600 columns; the default is 180.
- **Bayer** — choose a 4 × 4 or 8 × 8 dithering matrix.
- **Key** — choose the chroma-key color.
- **Key threshold** — controls how close a pixel must be to the key color to be removed.
- **Key softness** — feathers the key transition.
- **Foreground cutoff** — removes low-confidence foreground pixels.
- **Green dominance** — adjusts green-screen separation strength.
- **Spill suppression** — reduces key-color spill around the subject.
- **Background opacity** — controls the composited background opacity.
- **Tint strength** and **Tint color** — blend the source tones toward the selected tint.
- **Glitch** and **Noise** — add optional animated finish variation.
- **Contrast** — increases or reduces tonal separation.
- **Edge** — emphasizes flower contours.
- **Local contrast** — emphasizes differences between nearby cells.
- **Crease** — strengthens darker folds and petal creases.
- **Subject boost** — raises the visual priority of the foreground subject.

Values shown beside sliders use a 0–100 scale and can be edited directly.

### Finish

- **Glyph ramp** — customize the character sequence used by `ascii` mode, from light to dark coverage.

### Playback

- **Restart** — returns the source video to the beginning.
- **Reverse loop** — plays the video forward and backward to create an open-to-close loop.

### Overlays

- **Source video** — places the blurred original video beneath the rendered layer.
- **Sample background** — samples the video corners to set a color key.
- **Scanlines**, **Vignette**, and **Matte** — toggle the corresponding display overlays and diagnostics.

### Source

- **Load video** — loads a local video file as the live source.
- **Defaults** — restores the editor settings to their defaults.

### Export

- **Export WebM** — exports the editor composition as a fixed-frame-rate WebM when browser VP9 WebCodecs are available.
- **Export GIF** — exports the editor composition as a GIF in the browser.

Both exports include the active render style, background, overlays, source-video layer, and reverse-loop duration. `FPS` in the top bar shows the live frame rate.

## Project structure

```text
index.html            # GitHub Pages entry point
outputs/index.html    # editor application
outputs/flower.mp4    # default source video
```

## Notes

The editor is a static browser application and does not require a backend. WebM export depends on browser WebCodecs support; GIF export is available as a browser-side fallback.
