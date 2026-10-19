# Art

Sources for the four wallpapers in `backgrounds/`. All four were made for this theme by Parker
Brown with ChatGPT on 2026-10-19, at 1672×941.

| Wallpaper | Source |
|---|---|
| `1-the-meek-warrior.webp` | `the-meek-warrior.png` |
| `2-the-cell.webp` | `the-cell.png` |
| `3-the-lamp.webp` | `the-lamp.png` |
| `4-praus.webp` | `praus.png` |

## One repair

In the knight's source, the round window under the cross lets in light shaped like a skull. The
shipped wallpaper paints that shape out: the glyph is covered with the wall's own stone colour
and a plain lit disc in the window's sky colour takes its place, about 400 pixels of the
original. `the-meek-warrior.png` is kept exactly as made.

## The grade

Each image is upscaled with Lanczos to fill 3840×2160, then brightness and saturation are scaled
and the black point lifted, so the shadows land on the palette's true black.

| Wallpaper | Brightness | Saturation | Black point | Mean luma, source → graded |
|---|---|---|---|---|
| The Meek Warrior | 92% | 90% | 3% | 9.3% → 6.6% |
| The Cell | 96% | 92% | 2% | 6.6% → 5.1% |
| The Lamp | 100% | 94% | 1% | 2.9% → 2.3% |
| ΠΡΑΫΣ | 100% | 95% | 1% | 4.0% → 3.2% |

From the repository root, with ImageMagick 7. The knight takes the repair first; the seed makes
the stone's grain, and so the file, reproducible.

```sh
magick art/the-meek-warrior.png -crop 120x120+990+140 +repage -colorspace Gray -threshold 55% -morphology Dilate Disk:2 \( -size 1672x941 xc:black \) +swap -geometry +990+140 -compose over -composite -blur 0x1 /tmp/praus-skullmask.png
```
```sh
magick art/the-meek-warrior.png \( -size 1672x941 xc:'#141413' -seed 1 -attenuate 0.25 +noise Gaussian /tmp/praus-skullmask.png -alpha off -compose CopyOpacity -composite \) -compose over -composite \( -size 1672x941 xc:none -fill '#CDDAE1' -draw 'circle 1037,186 1037,171' -blur 0x1.4 \) -compose over -composite /tmp/praus-knight.png
```
```sh
magick /tmp/praus-knight.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 92,90,100 -level 3%,100% -strip -quality 90 -define webp:method=6 backgrounds/1-the-meek-warrior.webp
```
```sh
magick art/the-cell.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 96,92,100 -level 2%,100% -strip -quality 90 -define webp:method=6 backgrounds/2-the-cell.webp
```
```sh
magick art/the-lamp.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 100,94,100 -level 1%,100% -strip -quality 90 -define webp:method=6 backgrounds/3-the-lamp.webp
```
```sh
magick art/praus.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 100,95,100 -level 1%,100% -strip -quality 90 -define webp:method=6 backgrounds/4-praus.webp
```

The word is ΠΡΑΫΣ, the capital form of πραΰς as the lexicon gives it (Strong's 4239); the
lettering in `praus.png` was checked letter by letter, diaeresis included.
