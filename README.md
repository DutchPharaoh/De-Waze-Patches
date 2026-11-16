# De-Waze Patches

A collection of Morphe patches that add features to Waze.

## Patches

- **Favorites on map**: always shows your favorites as stars with their name on the map,
  on the phone and in Android Auto, also when you are not navigating.
  Home and work are left out, because Waze already shows those.

Supported version: Waze 5.27.4.900. The patches rely on obfuscated Waze internals,
so every new Waze version needs a check before it is added.

## Use in Morphe Manager

Add `https://github.com/DutchPharaoh/De-Waze-Patches` as a patch source in Morphe Manager, next to your other sources,
and select the patches you want when patching Waze.

<!-- PATCHES_START EXPANDED -->
> **[v1.0.0](https://github.com/DutchPharaoh/De-Waze-Patches/releases/tag/v1.0.0)**&nbsp;&nbsp;•&nbsp;&nbsp;`main`&nbsp;&nbsp;•&nbsp;&nbsp;1 patches total
<details open>
<summary>📦 Waze&nbsp;&nbsp;•&nbsp;&nbsp;1 patch</summary>
<br>

**Package name:** `com.waze`

**🎯 Supported versions:**

| 5.27.4.900 |
| :---: |

| 💊&nbsp;Patch | 📜&nbsp;Description | ⚙️&nbsp;Options |
|----------|----------------|-----------|
| [Favorites on map](#favorites-on-map) | Always shows your favorites as stars with their name on the map, on the phone and in Android Auto, also when not navigating. |  |

</details>

<!-- PATCHES_END -->

## Development

Building needs a GitHub token with `read:packages` in `~/.gradle/gradle.properties`
(`gpr.user` and `gpr.key`). Then run:

```
./gradlew build
```

### Layout

- `patches/src/main/kotlin/app/dewaze/patches/<feature>/`: one folder per patch
  (the patch itself plus its fingerprints).
- `patches/src/main/kotlin/app/dewaze/patches/shared/`: code shared by all patches,
  such as the supported Waze versions.
- `extensions/extension/src/main/java/app/dewaze/extension/`: the Java code the patches call at runtime.

To add a patch, create a new folder under `patches/.../patches/` and, if it needs runtime logic,
a matching class in the extension.

### Favorites on map

The patch adds three small hooks; all logic lives in
`extensions/extension/src/main/java/app/dewaze/extension/FavoritesOnMapPatch.java`.
If the stars do not show, check `adb logcat -s WazeFavoritesOnMap`.

This project is based on the Morphe patches template; see [NOTICE](NOTICE) and [LICENSE](LICENSE).
