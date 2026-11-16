# Waze Favorites Patches

Morphe patches for Waze.

## Patches

- **Favorites on map**: always shows your favorites as stars with their name on the map,
  on the phone and in Android Auto, also when you are not navigating.
  Home and work are left out, because Waze already shows those.

Supported version: Waze 5.27.4.900. The patch relies on obfuscated Waze internals,
so every new Waze version needs a check before it is added.

## Use in Morphe Manager

Add `https://github.com/DutchPharaoh/De-Waze-Patches` as a patch source in Morphe Manager, next to your other sources,
and select **Favorites on map** when patching Waze.

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

The patch adds three small hooks; all logic lives in
`extensions/extension/src/main/java/app/wazefav/extension/FavoritesOnMapPatch.java`.
If the stars do not show, check `adb logcat -s WazeFavoritesOnMap`.

This project is based on the Morphe patches template; see [NOTICE](NOTICE) and [LICENSE](LICENSE).
