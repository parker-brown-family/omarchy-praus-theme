# Art

Sources for the four wallpapers in `backgrounds/`.

| Wallpaper | Source | Made |
|---|---|---|
| `1-the-meek-warrior.webp` | `the-meek-warrior.png` (1672×941) | Parker Brown, ChatGPT, 2026-10-16 |
| `2-the-cell.webp` | `the-cell.png` (7680×4320 master) | Parker Brown, ChatGPT, 2026-10-16 |
| `3-the-lamp.webp` | `the-lamp.png` (1672×941) | Parker Brown, ChatGPT, 2026-10-16 |
| `4-praus.webp` | `praus.svg` | Set in Noto Serif Display Light, bronze `#A18C60` on black |

## The grade

Each painting is resized with Lanczos to fill 3840×2160 (the knight and the lamp upscaled from 1672×941, the cell downscaled from its 8K master), then brightness and saturation are scaled and the black point lifted, so the shadows land on the palette's true black.

| Wallpaper | Brightness | Saturation | Black point | Mean luma, source → graded |
|---|---|---|---|---|
| The Meek Warrior | 96% | 90% | 2% | 7.1% → 5.8% |
| The Cell | 100% | 95% | 1% | 5.0% → 4.2% |
| The Lamp | 100% | 94% | 1% | 3.1% → 2.5% |

From the repository root, with ImageMagick 7:

```sh
magick art/the-meek-warrior.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 96,90,100 -level 2%,100% -strip -quality 90 -define webp:method=6 backgrounds/1-the-meek-warrior.webp
```
```sh
magick art/the-cell.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 100,95,100 -level 1%,100% -strip -quality 90 -define webp:method=6 backgrounds/2-the-cell.webp
```
```sh
magick art/the-lamp.png -filter Lanczos -resize 3840x2160^ -gravity center -extent 3840x2160 -modulate 100,94,100 -level 1%,100% -strip -quality 90 -define webp:method=6 backgrounds/3-the-lamp.webp
```
```sh
rsvg-convert art/praus.svg | magick - -strip -define webp:lossless=true backgrounds/4-praus.webp
```

The word is ΠΡΑΫΣ, the capital form of πραΰς as the lexicon gives it (Strong's 4239).
