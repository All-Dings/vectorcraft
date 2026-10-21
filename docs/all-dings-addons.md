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
