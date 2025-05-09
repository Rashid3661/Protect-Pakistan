# India Content Blocker Chrome Extension

This Chrome extension blocks websites, content, and creators originating from India. It is intended for **personal use only** and should not be published on the Chrome Web Store due to its use of `webRequestBlocking` in Manifest V3.

## Features

- Blocks a predefined list of Indian news sites, entertainment platforms, e-commerce sites, government portals, and specific YouTube channels.
- Blocks all domains ending with the `.in` TLD.
- Redirects blocked requests to a custom "Content Blocked" page.
- Provides a popup with extension status.

## Files

- `manifest.json`: Extension configuration.
- `background.js`: Contains the blocking logic and the list of sites to block.
- `popup.html`/`popup.css`: UI for the extension's icon popup.
- `blocked.html`/`blocked.css`: Custom page displayed when content is blocked.
- `icons/`: Folder for extension icons (icon16.png, icon48.png, icon128.png). **You need to add these image files yourself.**

## Setup Instructions

1.  **Create Icons**:
    *   Create three PNG icon files: `icon16.png` (16x16 pixels), `icon48.png` (48x48 pixels), and `icon128.png` (128x128 pixels).
    *   Place these files into the `icons` folder within your `india-content-blocker` directory.

2.  **Download/Copy Files**:
    *   Create a folder named `india-content-blocker`.
    *   Save all the provided code files (`manifest.json`, `background.js`, `popup.html`, `popup.css`, `blocked.html`, `blocked.css`, `README.md`) into this folder, maintaining the structure (e.g., `icons` subdirectory).

3.  **Load the Extension in Chrome**:
    *   Open Google Chrome.
    *   Go to `chrome://extensions`.
    *   Enable "Developer mode" using the toggle switch, usually in the top-right corner.
    *   Click on the "Load unpacked" button.
    *   Navigate to and select the `india-content-blocker` folder you created.
    *   The extension should now be loaded and active. You'll see its icon in the Chrome toolbar.

## Modifying the Block List

1.  Open the `background.js` file in a text editor.
2.  Find the `const blockList = [...]` array.
3.  Add or remove URL patterns as needed. Follow the wildcard format (e.g., `"*://*.example.com/*"`).
4.  After saving changes to `background.js`, go back to `chrome://extensions` and click the "reload" (circular arrow) button for the "India Content Blocker" extension to apply the changes.

## Important Notes

-   **Personal Use**: This extension is designed for personal use.
-   **Broad Blocking**: The rule `"*://*.in/*"` is very broad and will block all websites using the `.in` top-level domain. Be mindful of this if you need to access legitimate `.in` sites not related to the content you wish to block. You can remove or comment out this line in `background.js` if it's too restrictive.
-   **YouTube Channels**: Blocking YouTube channels is based on their URL patterns (e.g., `youtube.com/channel/CHANNEL_ID` or `youtube.com/@HandleName`). This will block the channel page itself. It may not block individual videos from these channels if they are embedded or accessed via URLs that don't include the channel ID/name directly in a way that matches the pattern. More sophisticated YouTube blocking would require content scripts and potentially API usage.
-   **Performance**: A very long block list can potentially have a minor impact on browsing performance, though `webRequest` is generally efficient for this.

This setup should get your "India Content Blocker" extension running locally.