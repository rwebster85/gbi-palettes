# GBI Palette Converter

A browser-based tool for converting hex colours to the XRGB R5G5B5 palette format used by [Game Boy Interface](https://www.gc-forever.com/wiki/index.php?title=Game_Boy_Interface) (GBI), developed by Extrems.

**🔗 [Try it here](https://rwebster85.github.io/gbi-palettes/)**

---

## What it does

Game Boy Interface accepts a `--palette` argument in its `.cli` file to apply a custom 4-colour palette to Game Boy games. The format uses 16-bit XRGB R5G5B5 colour values:

```
--palette=#XXXX,#XXXX,#XXXX,#XXXX
```

Each colour is encoded using the formula:

```
0x8000 | ((r >> 3) << 10) | ((g >> 3) << 5) | (b >> 3)
```

This tool lets you pick colours using a standard hex colour picker or by entering hex values directly, then generates the correct `--palette` argument ready to paste into your `.cli` file.

---

## Features

- **Hex to XRGB conversion** — enter any hex colour and get the correct XRGB value
- **Live preview** — see your palette applied to classic Game Boy screenshots in real time
- **Hex/XRGB preview toggle** — compare your original hex colours against the converted XRGB values to spot any differences from the lossy conversion
- **Preset palettes** — includes a selection of hardware, custom emulator, and Super Game Boy palettes
- **Reverse conversion** — paste an existing `--palette=` string to convert XRGB codes back to approximate hex values
- **Shareable URLs** — share your palette via URL in either hex or XRGB format
- **Collapsible conversion breakdown** — view the R5/G5/B5 channel values for each colour

---

## Preset palettes

### Hardware
| Name | Description |
|---|---|
| DMG (NSO) | Original Game Boy, as used by Nintendo Switch Online |
| GB Pocket | Game Boy Pocket |
| GB Light | Game Boy Light |

### Custom
| Name | Description |
|---|---|
| DMG (Retroarch) | DMG palette as used by Retroarch |
| DMG (BGB) | DMG palette as used by the BGB emulator |
| GB Pocket (Retroarch) | GB Pocket palette as used by Retroarch |
| GB Light (Retroarch) | GB Light palette as used by Retroarch |

### Super Game Boy
| Name | Description |
|---|---|
| Metroid II (SGB) | Default SGB palette for Metroid II: Return of Samus |
| Metroid II Alt (SGB) | Alternative layer ordering for Metroid II |
| Mega Man V (SGB) | Default SGB palette for Mega Man V |
| Mega Man V Neptune Alt (SGB) | Neptune stage palette variant from Mega Man V |
| Link's Awakening DX (SGB) | SGB palette for The Legend of Zelda: Link's Awakening DX |

---

## Notes on conversion

- The R5G5B5 format uses 5 bits per channel, so converting from 8-bit hex drops the 3 least significant bits of each channel. This means reverse conversion back to hex is approximate and may not exactly match the original colour.
- The tool previews both the original hex colours and the converted XRGB colours so you can see any differences before copying the palette argument.
- Palette layer order follows the GBI `--palette` argument order: Layer 4, Layer 3, Layer 2, Layer 1.

---

## Usage

1. Open the tool at [rwebster85.github.io/gbi-palettes](https://rwebster85.github.io/gbi-palettes/)
2. Select a preset palette or enter your own hex colours
3. Copy the generated `--palette=` argument
4. Add it to your GBI `.cli` file

---

## Self-contained

The tool is a single HTML file with no external dependencies. All preview images are embedded as pre-quantised 2bpp pixel data and decoded at runtime.
