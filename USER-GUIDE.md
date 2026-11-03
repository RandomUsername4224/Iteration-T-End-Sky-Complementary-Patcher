# Iteration T — User Guide

## Overview

Iteration T adds an animated planet and rings, stars, a black hole and accretion disc to the End sky of supported Complementary-based shader packs. It also adds related End-lighting, colour and shadow controls.

## Requirements

- Windows 10 or later for the included graphical launcher.
- Python 3.11 or newer, with Tcl/Tk support enabled.
- No third-party Python packages are required.

Download Python from the [official Windows downloads page](https://www.python.org/downloads/windows/). Use the standard 64-bit Windows installer, not the embeddable ZIP. Keep Tcl/Tk support selected during installation.

To check your setup, open Command Prompt and run:

```bat
py --version
py -m tkinter
```

The first command should report Python 3.11 or newer. The second should open a small test window.

## Compatible shader packs

- Complementary Reimagined r5.9.3.
- Euphoria Patches 1.10.5 applied to Complementary Reimagined r5.9.3.

Use an original, unmodified source pack. Other releases may have different internal files and are not guaranteed to work. Do not use a source pack that already has Iteration T installed.

## Install on Windows

1. Download `Iteration-T-Installer.zip` from the [project's main page](README.md).
2. Extract the ZIP to a normal folder. Do not run it from inside the ZIP preview.
3. Open the extracted `Iteration T` folder.
4. Double-click `Start Iteration T.bat`.
5. Select the original Complementary ZIP or extracted shader-pack folder. For Euphoria, select the extracted Euphoria + Complementary shader-pack folder.
6. Follow the patcher's prompts. It creates a new output beside the source; it does not edit the selected source pack.
7. In Minecraft, open **Options → Video Settings → Shader Packs** and select the newly created shader pack.

If an output with the same name already exists, the patcher chooses another output name instead of overwriting it.

## Command-line use

From the extracted `Iteration T` folder:

```bat
py -3 patch.py "C:\path\to\original-shader-pack.zip" "C:\path\to\Iteration-T-output.zip"
```

For an extracted shader-pack folder, use its path as the first argument and a new output-folder path as the second. The output path must not already exist.

On macOS or Linux, use `python3` instead of `py -3`. The command-line patcher does not require Tk; the graphical launcher does.

## Iteration T settings

The following defaults are shipped with this release.

| Setting | What it does | Default |
|---|---|---:|
| End Sky Brightness | Changes the brightness of the Iteration T sky, including stars, planet, rings and black hole. | 100% |
| End Lighting Brightness | Changes the brightness of End block lighting and ambient light. | 150% |
| End Direct Light Brightness | Changes the strength of direct End light from the black-hole direction. | 350% |
| End Light Colour Neutrality | Controls the purple tint on End lighting and the Iteration T sky. Lower values add more purple; 100 removes the extra sky tint. | 100 |
| Black Hole and Accretion Disc | Shows or hides the black hole and its disc. | On |
| Black Hole Intensity | Changes the brightness of the black hole and its disc. | 100% |
| Black Hole Height | Moves the black hole and disc higher or lower in the sky. | 30° |
| Accretion Disc Left/Right Tilt | Tilts the disc from side to side. | -15° |
| Accretion Disc Up/Down Tilt | Tilts the disc up or down. | 20° |
| Gravitational Lensing | Controls how strongly light bends around the black hole. | 100% |
| Iteration T Stars | Shows or hides the generated star field. | On |
| Star Intensity | Changes how bright the stars appear. | 100% |
| Ringed Planet | Shows or hides the planet and its rings. | On |
| Planet Intensity | Changes the brightness of the planet and its rings. | 100% |
| Planet Orbit Tilt | Changes the tilt of the planet's orbital path. | 0° |
| Planet Orbit Phase | Sets the planet's starting position along its orbit. | 130° |
| Planet Cycle (minutes) | Sets the time for one complete orbit at 100% Animation Speed. Higher values slow the orbit; 250 minutes pauses it. | 20 minutes |
| Animation Speed | Changes the speed of the planet, stars and accretion-disc animations. | 100% |
| Sky Rotation | Rotates the whole Iteration T sky around the horizon. | 0° |
| Sky Tilt | Tilts the whole Iteration T sky up or down. | 0° |

### Additional Euphoria defaults

The Euphoria build also sets these Euphoria-specific defaults:

| Setting | Default |
|---|---:|
| Dragon Death Effect | 2 |
| End Crystal Vortex | 3 |
| End Flash | 1 |
| End Night Desaturation amount | 300 |
| Pixelated Shadows | On |
| Pixelated Water Reflections | On |
| Shadow Smoothing | 2 |

The End Night Desaturation amount is preset without enabling its separate master toggle.

## Finding the settings

Open the shader options, navigate to the End settings, and select **Iteration T**. The group contains the planet, stars, black hole, disc, sky and lighting controls.

Some shader loaders retain saved option values from earlier installations. If the packaged defaults do not appear, select the new shader pack and use **Reset Shader Settings** in the shader menu.

## Troubleshooting

### The launcher does not open

- Confirm Python 3.11 or newer is installed.
- Run `py -m tkinter` to check that Tk is available.
- If `py` is not recognised, reinstall Python using the official Windows installer and enable the Python launcher.

### The patcher says the source pack is unsupported

- Select an extracted shader-pack folder or ZIP archive.
- Use an original, unmodified compatible source pack.
- For Euphoria, select the extracted Euphoria + Complementary shader-pack folder, not the Euphoria Patcher program ZIP.
- Do not select a pack that already contains Iteration T.

### The new settings or defaults are missing

- Make sure Minecraft is using the newly generated shader pack, not the original source.
- Reset the selected shader pack's saved settings if necessary.

### The shader fails to compile

- Confirm the source pack is one of the compatible releases listed above.
- Test without other shader modifications first.
- When reporting an issue, include your Minecraft version, shader loader, source-pack type and the complete shader compilation error.

## Performance note

The custom End shadow direction needs off-screen objects to remain eligible as shadow casters. Iris' `shadow.culling` setting is therefore disabled in the pack configuration. This setting applies pack-wide rather than only in the End and may increase shadow-pass work in the Overworld and Nether. Normal camera frustum culling for visible scene rendering remains enabled.

## Safety and backups

The patcher creates a new output and does not modify the selected source pack. Keep the original shader pack as a backup and install the generated copy separately.
