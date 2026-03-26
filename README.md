# Gemini Watermark Remover

A client-side web tool that removes the visible sparkle watermark from Gemini-generated images.

## How it works

Google Gemini applies a fixed sparkle watermark to all generated images at a known position (bottom-right corner). This tool reverses the alpha blending using pre-extracted alpha maps to reconstruct the original pixels.

The formula: `original = (watermarked - alpha * 255) / (1 - alpha)`

- **48x48** alpha map + 32px margin for images where either dimension is 1024 or smaller
- **96x96** alpha map + 64px margin for images where both dimensions exceed 1024

## Features

- Drag & drop or browse to upload images
- Batch processing — upload and process multiple images at once
- Download individual images or all at once
- Runs entirely in the browser — no server, no uploads to third parties

## Usage

Open `index.html` in a browser. That's it — no build step, no dependencies.

Or serve it locally:

```sh
python3 -m http.server 8080
```

## Limitations

- Only removes the visible sparkle watermark, not the invisible SynthID watermark embedded in pixel data
- Alpha maps are extracted from a specific Gemini version and may need updating if Google changes the watermark
