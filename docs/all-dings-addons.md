# All-Dings Addons

## Host-supplied linked images (control-protocol.md)

`links.openExternal {reference, name, dataBase64}` opens a raster image linked
with an ordinary relative filename. Native callers may supply `path` instead
of bytes. `reference` is a single ASCII basename (letters, digits, dots,
underscores, hyphens; excluding `.` and `..`). No URI scheme is stored.
The existing LinkInfo checksum and preview are retained. Unmodified native
VectorCraft can load these files when the images are beside the project.

`links.external {}` lists unresolved image link paths across open documents.
`links.supplyExternal {reference, name, dataBase64}` (or `path`) restores
original pixels only when the saved checksum and image key match. It preserves
the link and does not mark the project dirty or create an undo step. Successful
supply removes the corresponding entry from a native missing-link prompt.
Adapters must authorize identifiers before fetching bytes. No engine network
requests occur. Normal native link updates retain upstream behavior, including
its policy for changed files. Copy/paste preserves links. Include Linked Files
can embed originals. These commands work through native control and the web API.

## Canvas geometry for browser input replay

The document canvas rounds its rectangle to device pixels before painting,
inspection and screen-to-document pointer mapping. Fresh egui dock layouts can
otherwise differ by 1/32 of a CSS pixel, moving document coordinates even when
the viewport and pointer positions match. This change has no Dings dependency
and adds no control method. A headless regression covers subpixel dock width
variation and verifies that a real pixel resize still changes the mapping.

The keyboard/mouse recorder, SM serialization, playback scheduler and controls
live in the external ArtCraft wrapper. The wrapper uses the existing web API
for initialization and inspection and the browser input path for event replay.
