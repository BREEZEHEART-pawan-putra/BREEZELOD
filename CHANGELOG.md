# Changelog

## 0.1.2-alpha
- Increased configured chunk radius default and maximum from 8/12 to 32 chunks.
- Updated documentation to note higher potential rendering cost at the larger radius.

## 0.1.1-alpha
- Added sampled/cached surface data to reduce repeated per-frame block lookups.
- Added H toggle key and HUD state indicator.
- Added properties config for enable state, sample resolution, radius, and refresh period.
- Added cache cleanup on chunk unload and when entries leave the scan radius.
- Added common OpenGL state restoration and skip-on-runtime-error map-color sampling.
- Updated build resource expansion and documentation.

## 0.1.0-alpha
- Initial loaded-chunk surface overlay prototype.
