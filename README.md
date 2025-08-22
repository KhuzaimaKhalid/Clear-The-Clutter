# Clear-The-Clutter

# organize-files

A small Node.js script to organize files in a folder by moving non-JS/JSON files into extension-named subfolders (e.g. `mp4/`, `png/`).

## What it does

* Reads a target folder (defaults to the script folder).
* Skips files without extensions and files ending in `.js` or `.json`.
* For every other file it finds, it creates (if needed) a subfolder named after the file extension and moves the file into it.

## Requirements

* Node.js 18+ (tested on Node 22)

## Installation

1. Put `index.js` into your project folder (or use the provided version).
2. If you want to use `import` syntax without warnings, add this to your `package.json`:

```json
{
  "type": "module"
}
```

Or rename `index.js` to `index.mjs` and run using Node.

## Usage

Run from the folder containing `index.js` (default mode):

```bash
node index.js
```

Or pass a folder path you want to organize:

```bash
node index.js "D:\\Harry Sigma Course\\video_93"
```

Notes:

* The script will create extension folders *inside* the target folder (e.g. `target/mp4/`).
* It awaits file operations so moves are completed before the script exits.
* It intentionally skips `.js` and `.json` files to avoid moving the script or its config.

## Example

Before:

```
video_93/
  index.js
  clip.mp4
  notes.txt
  image.png
```

After running:

```
video_93/
  index.js
  mp4/clip.mp4
  txt/notes.txt
  png/image.png
```

## Troubleshooting

* **ENOENT (no such file or directory)**: verify the path you pass exists. Use absolute paths to be safe.
* **Module type warning**: add `"type": "module"` to `package.json` or rename to `.mjs`.
* If files don't move, check permissions and that no other program is locking the files.

## License & Author

MIT — feel free to reuse and modify.

Made by Khuzaima Khalid — happy to help if you want a dry-run option or additional filters.
