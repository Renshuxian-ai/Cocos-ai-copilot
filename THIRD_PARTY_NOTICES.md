# Third-party notices

## Funplay Cocos MCP 0.6.3

- Upstream: https://github.com/FunplayAI/funplay-cocos-mcp
- License: MIT
- License text: `third_party/funplay-cocos-mcp/LICENSE`

Cocos AI Copilot includes a modified, project-scoped subset of the upstream
runtime: MCP transport, Cocos scene/asset/file tools, Preview input and capture,
tool-effect metadata, and supporting safety utilities. The subset is owned and
started by the Copilot extension; it is not installed or exposed as a second
Cocos Creator extension. Legacy internal IDs and metadata keys are retained
where changing them would break existing project Skills or review evidence.

The audio workflow vendors only the files required for WAV, MP3, and OGG
decode/encode support. It does not vendor the complete upstream repositories.

## audiojs/audio 2.9.0

- Upstream: https://github.com/audiojs/audio
- License: MIT
- Vendored entry: `third_party/audiojs/2.9.0/audio.mjs`
- License text: `third_party/audiojs/2.9.0/LICENSE.txt`

The following runtime packages are vendored under
`third_party/audiojs/2.9.0/node_modules` because `audio.mjs` loads codecs on
demand:

| Package | Version | License |
| --- | ---: | --- |
| `@audio/decode-mp3` | 1.3.1 | MIT |
| `@audio/decode-vorbis` | 1.3.4 | MIT |
| `@audio/decode-wav` | 2.0.0 | MIT |
| `@audio/encode-mp3` | 2.0.0 | MIT |
| `@audio/encode-ogg` | 1.3.0 | MIT |
| `@audio/encode-wav` | 1.5.2 | MIT |

Each package directory retains its upstream `LICENSE` file.

Those codec bundles include the following transitive runtime components:

| Package | Version | License |
| --- | ---: | --- |
| `@swc/helpers` | 0.5.23 | Apache-2.0 |
| `simple-yenc` | 1.0.4 | MIT |
| `@wasm-audio-decoders/common` | 9.0.7 | MIT |
| `@wasm-audio-decoders/ogg-vorbis` | 0.1.20 | MIT |
| `codec-parser` | 2.5.0 | LGPL-3.0-or-later |
| `mpg123-decoder` | 1.0.3 | MIT |
| `wasm-media-encoders` | 0.7.0 | MIT |

Additional retained license texts are in
`third_party/audiojs/2.9.0/LICENSES`. `codec-parser` remains readable in the
vendored JavaScript codec module; its upstream source is available at
https://github.com/eshaz/codec-parser.

## Jimp 1.6.0 image-processing modules

The 2D Image Toolkit uses the slim, CommonJS-compatible Jimp building blocks
listed below instead of the full Jimp convenience bundle. All listed Jimp
packages are version 1.6.0 and licensed under the MIT License. Their upstream
license texts remain in the corresponding `node_modules/@jimp/*/LICENSE`
files.

| Package | Purpose |
| --- | --- |
| `@jimp/core` | Bitmap core and codec/plugin composition |
| `@jimp/js-jpeg` | JPEG decode and encode |
| `@jimp/js-png` | PNG decode and encode |
| `@jimp/plugin-blit` | Bitmap composition |
| `@jimp/plugin-color` | Color transforms |
| `@jimp/plugin-contain` | Aspect-preserving contain resize |
| `@jimp/plugin-crop` | Rectangular crop |
| `@jimp/plugin-flip` | Horizontal and vertical flip |
| `@jimp/plugin-mask` | Bitmap masking |
| `@jimp/plugin-resize` | Nearest and smooth resize |
| `@jimp/plugin-rotate` | Quarter-turn rotation |

Jimp loads the following runtime dependencies. Exact versions are locked by
`package-lock.json`; license files distributed by each package remain in its
`node_modules` directory. `@tokenizer/token` and
`readable-web-to-node-stream` distribute the complete MIT text in their
README files. The RC also retains that exact text as a separate `LICENSE`.

| Package | Version | License |
| --- | ---: | --- |
| `@jimp/file-ops` | 1.6.0 | MIT |
| `@jimp/types` | 1.6.0 | MIT |
| `@jimp/utils` | 1.6.0 | MIT |
| `@tokenizer/token` | 0.3.0 | MIT |
| `abort-controller` | 3.0.0 | MIT |
| `await-to-js` | 3.0.0 | MIT |
| `base64-js` | 1.5.1 | MIT |
| `buffer` | 6.0.3 | MIT |
| `event-target-shim` | 5.0.1 | MIT |
| `events` | 3.3.0 | MIT |
| `exif-parser` | 0.1.12 | MIT |
| `file-type` | 16.5.4 | MIT |
| `ieee754` | 1.2.1 | BSD-3-Clause |
| `jpeg-js` | 0.4.4 | BSD-3-Clause |
| `mime` | 3.0.0 | MIT |
| `peek-readable` | 4.1.0 | MIT |
| `pngjs` | 7.0.0 | MIT |
| `process` | 0.11.10 | MIT |
| `readable-stream` | 4.7.0 | MIT |
| `readable-web-to-node-stream` | 3.0.4 | MIT |
| `safe-buffer` | 5.2.1 | MIT |
| `string_decoder` | 1.3.0 | MIT |
| `strtok3` | 6.3.0 | MIT |
| `tinycolor2` | 1.6.0 | MIT |
| `token-types` | 4.2.1 | MIT |
| `zod` | 3.25.76 | MIT |

Jimp upstream: https://github.com/jimp-dev/jimp

## Panzoom 4.6.2

- Upstream: https://github.com/timmywil/panzoom
- License: MIT
- Runtime: `third_party/panzoom/4.6.2/panzoom.cjs`
- Full license: `third_party/panzoom/4.6.2/LICENSE.txt`

## Native audio components embedded in the WASM codecs

The MIT licenses of the JavaScript wrappers do not replace the licenses of
their underlying codec implementations. The encoder build uses LAME, libogg
and libvorbis. The decoder build uses mpg123, libogg and libvorbis.
The retained upstream COPYING files in `third_party/audiojs/2.9.0/LICENSES`
include LAME (LGPL), mpg123 (LGPL-2.1), libogg/libvorbis (BSD), and the puff
decompressor's zlib-style notice. Provenance records identify
the exact encoder/decoder submodule commits used for these texts.
Do not interpret the wrapper's MIT metadata as an all-MIT audio stack.

## External Codex app-server prerequisite (not redistributed)

This Copilot extension does not bundle Codex, ripgrep, PCRE2, the code-mode
host, or Windows sandbox executables. It discovers a compatible Codex
installation already present on the user's computer and invokes its app-server
mode. Discovery does not download or install Codex. If no compatible executable
is available, Copilot displays an actionable installation/update message.

The external Codex installation retains its upstream licensing and updates.
Its Rust/native dependency inventory is not part of this Copilot distribution's
production dependency list. The compatibility manifest is integration metadata,
not an embedded runtime. This notice records engineering evidence, not a legal
opinion.

Upstream license download URLs and content hashes are recorded in
`third_party/license-provenance.json`. Third-party portions retain their own
licenses; the root MIT license applies to the project's own code.
