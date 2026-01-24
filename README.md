# Offline Bitcoin Block Verifier

A single-file Progressive Web App (PWA) for verifying Bitcoin blocks entirely offline. Download blocks while online, then verify their integrity without any network connection.

## Features

- **Block Verification** — Verifies transaction hashes, Merkle root, and block header hash
- **Transaction Viewer** — Browse transactions in a block, filter by address
- **Block Download** — Fetch blocks from public Bitcoin RPC endpoints
- **Hash File Management** — Maintain a local list of known block hashes for cross-verification
- **Built-in File Manager** — OPFS-based storage; import, export, and manage files without leaving the app
- **Fully Offline** — Service worker caches the app for offline use
- **Installable** — PWA manifest allows install on desktop and mobile

## How It Works

1. **Import or download** block data using the File Manager or Download Block section
2. **Load a hash file** (optional) containing known block hashes for extra verification
3. **Check a block** — the app independently verifies:
   - Each transaction's serialized hash matches its `txid`
   - The Merkle root computed from all `txid`s matches the block header
   - The double-SHA256 of the 80-byte header matches the block hash
   - The block hash matches your stored hash file (if loaded)

All cryptography uses the browser's native `crypto.subtle` API — no external libraries.

## File Structure

```
oflibit_aio.html   — The entire application (HTML + CSS + JS)
service-worker.js  — Caches the app for offline use
manifest.json      — PWA manifest
favicon.ico        — App icon
icon-192.png       — PWA icon (192x192)
icon-512.png       — PWA icon (512x512)
data/              — Sample block JSON files and hash list for testing
```

## Usage

Serve the files from any static web server (or open locally with a server for service worker support):

```bash
# Python
python -m http.server 8000

# Node
npx serve .
```

Then open `http://localhost:8000/oflibit_aio.html` in a modern browser.

### File Manager

The File Manager uses the browser's Origin Private File System (OPFS) to store files persistently. Files are organized into three categories:

| Category | Purpose |
|----------|---------|
| **Hashes** | Block hash list files (`.txt`, format: `height:  hash`) |
| **Blocks** | Downloaded block JSON files |
| **Verify** | Block files imported specifically for verification |

Import files from your device here, then use them in the other sections via the dropdown selectors.

### RPC Endpoints

The app ships with several public Bitcoin RPC endpoints pre-configured. You can also enter a custom endpoint (e.g., your own Bitcoin Core node).

## Browser Requirements

- Modern browser with `crypto.subtle` support (all current browsers)
- OPFS support for the File Manager (Chrome 86+, Firefox 111+, Safari 15.2+)
- Service Worker support for offline capability

## License

MIT
