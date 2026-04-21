Excalidraw canvas stack for Codex MCP.

- Canvas URL: http://127.0.0.1:3000
- Network: excalidraw
- Image: ghcr.io/yctimlin/mcp_excalidraw-canvas:latest

## Libraries

This stack runs a prebuilt Excalidraw canvas image. Libraries added from the Excalidraw UI are handled by the browser session, not by Docker.

- `Browse libraries` / `Add to Excalidraw` installs the library into the current browser profile.
- The library is not stored inside the container filesystem.
- Restarting the container is usually not what removes the library; opening the canvas in another browser or profile is.
- This behavior is suitable for personal/local use without customizing the image.

Example add-library URL:

`http://127.0.0.1:3000/#addLibrary=https%3A%2F%2Flibraries.excalidraw.com%2Flibraries%2FBjoernKW%2FUML-ER-library.excalidrawlib&token=...`

## MCP limitation

The current MCP canvas integration can create and edit canvas elements, but it does not import, list, or insert UI library items automatically.

- Skills can help define the diagram structure.
- The Excalidraw UI library must still be used manually in the browser.
- If shared persistence or agent-driven library usage is needed later, replace this prebuilt image with a custom Excalidraw app that persists `libraryItems` and handles `#addLibrary` directly.
