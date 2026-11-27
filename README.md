# BreezeLOD 0.1.1-alpha

**Minecraft:** 1.12.2  
**Forge:** 14.23.5.2860  
**Java:** 8  
**Purpose:** conservative, coarse cached surface overlay for low-end devices.

## Important limitation
This is still a **loaded-chunk surface overlay prototype**, not a true distant-terrain LOD mod. It does not request or generate chunks outside Minecraft's normal loaded area, so it cannot extend visibility beyond the vanilla/OptiFine render distance. The current version draws sampled surface quads from chunks already loaded by the game.

## Prototype improvements in 0.1.1-alpha
- Coarse surface sampling (default 8-block step, 4 samples per chunk).
- Cached sampled surface data instead of sampling every block every frame.
- Cache refreshes when the player changes chunk or at a configurable tick interval.
- Cache entries removed when chunks unload or leave the working radius.
- Configurable radius, sampling step, refresh interval, and enabled state.
- Toggle overlay with **H** (configurable in Minecraft Controls).
- Small HUD indicator for enabled/disabled status.
- Attempts to restore OpenGL state modified by the overlay.
- Conservative startup state (overlay disabled), radius default 32 chunks, sample step 8, cache refresh every 40 ticks. A 32-chunk radius can increase CPU/GPU work when many chunks are loaded; reduce it on weak devices if performance suffers.

## Configuration
File: `config/BreezeLOD.properties`

- `enabled=false` (starts off for performance; toggle with H)
- `chunkRadius=32` (clamped to 2–32)
- `sampleStep=8` (allowed: 2, 4, 8, 16)
- `refreshTicks=40` (clamped to 10–200)

## Build
Use a JDK 8 and a Gradle 4.x-era installation compatible with ForgeGradle 2.3.

```sh
gradle setupDecompWorkspace
gradle build
```
The output is expected under `build/libs/`.

## Compatibility/testing status
OptiFine, Android launchers, OpenGL ES translation backends, and other mods are not runtime-tested. Compatibility cannot be guaranteed. This prototype avoids replacing vanilla chunk-rendering internals, but render overlays can still interact with other render mods.
