# Complementary End Skybox Patcher — User Guide

## What this tool does

This tool patches a compatible Complementary-based shader pack to add the **Iteration T End skybox**: its animated ringed planet, stars, black hole, accretion disc and associated End lighting.

It is important to distinguish the projects: **Iteration T is the source of the End-sky effects. This download is a patcher for Complementary Reimagined, not the Iteration T shader pack itself.**

## Requirements

- Windows 10 or later for the graphical launcher.
- Python 3.11 or newer, with Tcl/Tk support enabled.
- No third-party Python packages are required; the patcher uses Python's standard library.

Download the standard 64-bit Windows installer from the [official Python downloads page](https://www.python.org/downloads/windows/). Keep Tcl/Tk support selected and enable the Python launcher if offered.

Check the installation in Command Prompt:

```bat
py --version
py -m tkinter
```

The first command should report Python 3.11 or newer. The second should open a small test window. Use the standard Windows installer, not the embeddable ZIP package.

## Supported source packs

- Complementary Reimagined r5.9.3.
- Euphoria Patches 1.10.5 applied to Complementary Reimagined r5.9.3.

Use an original, unmodified source pack. Other releases may have different internal files and are not guaranteed to be compatible. For Euphoria, select the extracted Euphoria + Complementary shader-pack folder, not the Euphoria Patcher program ZIP.

## Install on Windows

1. Download `Complementary-End-Skybox-Patcher.zip` from the [project repository](https://github.com/RandomUsername4224/Iteration-T-End-Sky-Complementary-Patcher).
2. Extract the ZIP to a normal folder; do not run it from inside the ZIP preview.
3. Open the extracted **Complementary End Skybox Patcher** folder.
4. Double-click **Start Patcher.bat**.
5. Select the original Complementary ZIP or its extracted shader-pack folder. For Euphoria, select the extracted Euphoria + Complementary shader-pack folder.
6. The patcher checks the source, applies the End-sky integration and creates a **new copy** beside the source. It does not modify the selected source pack.
7. In Minecraft, open **Options → Video Settings → Shader Packs** and select the newly created shader pack. Its name ends in `-End-Skybox`.

If an output with that name already exists, the patcher adds a number instead of overwriting it.

## Command-line use

From the extracted patcher folder:

```bat
py -3 patch_complementary.py "C:\path\to\original-shader-pack.zip" "C:\path\to\patched-shader-pack.zip"
```

For an extracted source folder, use that folder as the first argument and a new output-folder path as the second. The output path must not already exist. On macOS or Linux, use `python3` instead of `py -3`; the command-line patcher does not require Tk.

## Settings

In the shader options, open **End Settings → End Skybox**. The settings control the planet, stars, black hole, accretion disc, sky and related End lighting. Every tooltip states its default.

| Setting | What it does | Default |
|---|---|---:|
| End Sky Brightness | Changes the brightness of the complete End sky, including stars, planet, rings and black hole. | 100% |
| End Lighting Brightness | Changes the brightness of End block lighting and ambient light. | 150% |
| End Direct Light Brightness | Changes the strength of the direct End light coming from the black-hole direction. | 350% |
| End Light Colour Neutrality | Controls the purple tint on End lighting and all End-sky effects. Lower values add more purple; 100 removes the extra sky tint. | 100 |
| Black Hole and Accretion Disc | Shows or hides the black hole and its disc. | On |
| Black Hole Intensity | Changes the brightness of the black hole and its disc. | 100% |
| Black Hole Height | Moves the black hole and disc higher or lower in the sky. | 30° |
| Accretion Disc Left/Right Tilt | Tilts the disc from side to side. | -15° |
| Accretion Disc Up/Down Tilt | Tilts the disc up or down. | 20° |
| Gravitational Lensing | Controls how strongly light bends around the black hole. | 100% |
| Stars | Shows or hides the star field from the Iteration T skybox. | On |
| Star Intensity | Changes how bright the stars appear. | 100% |
| Ringed Planet | Shows or hides the planet and its rings. | On |
| Planet Intensity | Changes the brightness of the planet and its rings. | 100% |
| Planet Orbit Tilt | Changes the tilt of the planet's orbital path. | 0° |
| Planet Orbit Phase | Sets the planet's starting position along its orbit. | 130° |
| Planet Cycle (minutes) | Sets the time for one complete orbit at 100% Animation Speed. Higher values make the orbit slower; 250 minutes pauses it. | 20 minutes |
| Animation Speed | Changes the speed of the planet, stars and accretion-disc animations. | 100% |
| Sky Rotation | Rotates the complete End sky left or right around the horizon. | 0° |
| Sky Tilt | Tilts the complete End sky up or down. | 0° |

### Additional Euphoria defaults

The Euphoria build also applies these Euphoria-specific defaults:

| Setting | Default |
|---|---:|
| Dragon Death Effect | 2 |
| End Crystal Vortex | 3 |
| End Flash | 1 |
| End Night Desaturation amount | 300 |
| Pixelated Shadows | On |
| Pixelated Water Reflections | On |
| Shadow Smoothing | 2 |

The End Night Desaturation amount is preset without enabling its separate master toggle. The Euphoria `DEFAULT` profile is updated to match its applicable values.

If your shader loader has retained old per-pack settings, select the patched shader pack and use **Reset Shader Settings** so the packaged defaults can take effect.

## Troubleshooting

**The launcher does not open**
- Confirm Python 3.11 or newer is installed.
- Run `py -m tkinter` to check that Tk is available.
- If `py` is not recognised, reinstall Python using the official Windows installer and enable the Python launcher.

**The source pack is reported as unsupported**
- Select an extracted shader-pack folder or ZIP archive.
- Use one of the compatible original source packs listed above.
- For Euphoria, select the extracted Euphoria + Complementary shader-pack folder, not the Euphoria Patcher program ZIP.
- Do not select a pack that already has this End-sky integration.

**The new settings or defaults are missing**
- Make sure Minecraft is using the newly created `-End-Skybox` pack, not the original source pack.
- Reset the selected shader pack's saved settings if necessary.

**The shader fails to compile**
- Confirm that you used one of the compatible source-pack versions.
- Test without other shader modifications first; other patches may edit the same files.
- When reporting an issue, include your Minecraft version, shader loader, source-pack type and the complete shader compilation error.

## Performance note

The custom End light direction requires objects outside the camera view to remain eligible as shadow casters. Iris' `shadow.culling = false` setting is pack-wide, not dimension-specific, and may increase shadow-pass work in the Overworld and Nether. Normal camera frustum culling for visible scene rendering remains enabled.

## Safety and backups

The patcher creates a new output and does not modify the selected input. Keep the original shader pack as a backup and install the generated copy separately in Minecraft.
