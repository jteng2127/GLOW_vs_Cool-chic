# GLOW vs. Cool-chic on Kodak

Visual comparison of GLOW and Cool-chic 4.2.1 (WD + MSE) on all 24 Kodak images, at about 0.13 bpp.

Each image has two figures:

- `kodimNN_crop`: Ground Truth (full image, red box) | crop of Ground Truth | GLOW | Cool-chic (WD + MSE).
- `kodimNN_full`: full Ground Truth | GLOW | Cool-chic (WD + MSE).

Titles give bpp / PSNR (dB) / DISTS of the full image. PNG figures are in `png/`, PDF versions in `pdf/`, and the
crop windows and per-image numbers in `crops.json`.

## Settings

| | GLOW | Cool-chic (WD + MSE) |
| --- | --- | --- |
| Codec | DCAE (VAE-based, one model shared by all images) | Cool-chic 4.2.1, overfitted to each image |
| Starting point | DCAE MSE checkpoint (`0.05checkpoint_best.pth.tar`) | trained from scratch per image |
| Loss | λ·bpp + 0.25·WA-WD (σ = 32) + 0.1·LPIPS + 1.0·Grid Loss (period 16) | distortion + λ·rate, distortion = 0.8·WD (σ = 8) + 0.2·MSE (`--tune=wasserstein`) |
| Rate point | λ = 1.25, iteration 9000 | fixed λ = 0.28 for every image (not rate-matched per image) |
| Training | MLIC-Train-100K, 512² patches, batch 12, lr 1e-4 | `perceptive.cfg` (10k iterations, lr 1e-2), `hop.cfg` decoder |
| Kodak mean bpp / PSNR / DISTS | 0.1248 / 26.02 / 0.0633 | 0.1317 / 21.00 / 0.0782 |

- Bitrates are estimated, not measured on real bitstreams. GLOW: forward-pass entropy estimate. Cool-chic: the
  encoder's `rate_bpp`, with its encoder-side decoded image.
- PSNR is on 8-bit RGB. DISTS is the `pyiqa` implementation.
- Crops are 256 × 384 px for portrait images and 192 × 288 px for landscape ones. They sit on the 16-px grid and
  at least 16 px from every edge, because the Kodak files have a 1–3 px gray frame and a black last row or column.
  Each crop is picked automatically as the window that ranks high in both structure and texture: the density of
  strong edges, and the fine detail away from those edges. kodim04 uses a hand-picked crop.

## Figures

### kodim01

[`png/kodim01_crop.png`](png/kodim01_crop.png)

![kodim01_crop](png/kodim01_crop.png)

[`png/kodim01_full.png`](png/kodim01_full.png)

![kodim01_full](png/kodim01_full.png)

### kodim02

[`png/kodim02_crop.png`](png/kodim02_crop.png)

![kodim02_crop](png/kodim02_crop.png)

[`png/kodim02_full.png`](png/kodim02_full.png)

![kodim02_full](png/kodim02_full.png)

### kodim03

[`png/kodim03_crop.png`](png/kodim03_crop.png)

![kodim03_crop](png/kodim03_crop.png)

[`png/kodim03_full.png`](png/kodim03_full.png)

![kodim03_full](png/kodim03_full.png)

### kodim04

[`png/kodim04_crop.png`](png/kodim04_crop.png)

![kodim04_crop](png/kodim04_crop.png)

[`png/kodim04_full.png`](png/kodim04_full.png)

![kodim04_full](png/kodim04_full.png)

### kodim05

[`png/kodim05_crop.png`](png/kodim05_crop.png)

![kodim05_crop](png/kodim05_crop.png)

[`png/kodim05_full.png`](png/kodim05_full.png)

![kodim05_full](png/kodim05_full.png)

### kodim06

[`png/kodim06_crop.png`](png/kodim06_crop.png)

![kodim06_crop](png/kodim06_crop.png)

[`png/kodim06_full.png`](png/kodim06_full.png)

![kodim06_full](png/kodim06_full.png)

### kodim07

[`png/kodim07_crop.png`](png/kodim07_crop.png)

![kodim07_crop](png/kodim07_crop.png)

[`png/kodim07_full.png`](png/kodim07_full.png)

![kodim07_full](png/kodim07_full.png)

### kodim08

[`png/kodim08_crop.png`](png/kodim08_crop.png)

![kodim08_crop](png/kodim08_crop.png)

[`png/kodim08_full.png`](png/kodim08_full.png)

![kodim08_full](png/kodim08_full.png)

### kodim09

[`png/kodim09_crop.png`](png/kodim09_crop.png)

![kodim09_crop](png/kodim09_crop.png)

[`png/kodim09_full.png`](png/kodim09_full.png)

![kodim09_full](png/kodim09_full.png)

### kodim10

[`png/kodim10_crop.png`](png/kodim10_crop.png)

![kodim10_crop](png/kodim10_crop.png)

[`png/kodim10_full.png`](png/kodim10_full.png)

![kodim10_full](png/kodim10_full.png)

### kodim11

[`png/kodim11_crop.png`](png/kodim11_crop.png)

![kodim11_crop](png/kodim11_crop.png)

[`png/kodim11_full.png`](png/kodim11_full.png)

![kodim11_full](png/kodim11_full.png)

### kodim12

[`png/kodim12_crop.png`](png/kodim12_crop.png)

![kodim12_crop](png/kodim12_crop.png)

[`png/kodim12_full.png`](png/kodim12_full.png)

![kodim12_full](png/kodim12_full.png)

### kodim13

[`png/kodim13_crop.png`](png/kodim13_crop.png)

![kodim13_crop](png/kodim13_crop.png)

[`png/kodim13_full.png`](png/kodim13_full.png)

![kodim13_full](png/kodim13_full.png)

### kodim14

[`png/kodim14_crop.png`](png/kodim14_crop.png)

![kodim14_crop](png/kodim14_crop.png)

[`png/kodim14_full.png`](png/kodim14_full.png)

![kodim14_full](png/kodim14_full.png)

### kodim15

[`png/kodim15_crop.png`](png/kodim15_crop.png)

![kodim15_crop](png/kodim15_crop.png)

[`png/kodim15_full.png`](png/kodim15_full.png)

![kodim15_full](png/kodim15_full.png)

### kodim16

[`png/kodim16_crop.png`](png/kodim16_crop.png)

![kodim16_crop](png/kodim16_crop.png)

[`png/kodim16_full.png`](png/kodim16_full.png)

![kodim16_full](png/kodim16_full.png)

### kodim17

[`png/kodim17_crop.png`](png/kodim17_crop.png)

![kodim17_crop](png/kodim17_crop.png)

[`png/kodim17_full.png`](png/kodim17_full.png)

![kodim17_full](png/kodim17_full.png)

### kodim18

[`png/kodim18_crop.png`](png/kodim18_crop.png)

![kodim18_crop](png/kodim18_crop.png)

[`png/kodim18_full.png`](png/kodim18_full.png)

![kodim18_full](png/kodim18_full.png)

### kodim19

[`png/kodim19_crop.png`](png/kodim19_crop.png)

![kodim19_crop](png/kodim19_crop.png)

[`png/kodim19_full.png`](png/kodim19_full.png)

![kodim19_full](png/kodim19_full.png)

### kodim20

[`png/kodim20_crop.png`](png/kodim20_crop.png)

![kodim20_crop](png/kodim20_crop.png)

[`png/kodim20_full.png`](png/kodim20_full.png)

![kodim20_full](png/kodim20_full.png)

### kodim21

[`png/kodim21_crop.png`](png/kodim21_crop.png)

![kodim21_crop](png/kodim21_crop.png)

[`png/kodim21_full.png`](png/kodim21_full.png)

![kodim21_full](png/kodim21_full.png)

### kodim22

[`png/kodim22_crop.png`](png/kodim22_crop.png)

![kodim22_crop](png/kodim22_crop.png)

[`png/kodim22_full.png`](png/kodim22_full.png)

![kodim22_full](png/kodim22_full.png)

### kodim23

[`png/kodim23_crop.png`](png/kodim23_crop.png)

![kodim23_crop](png/kodim23_crop.png)

[`png/kodim23_full.png`](png/kodim23_full.png)

![kodim23_full](png/kodim23_full.png)

### kodim24

[`png/kodim24_crop.png`](png/kodim24_crop.png)

![kodim24_crop](png/kodim24_crop.png)

[`png/kodim24_full.png`](png/kodim24_full.png)

![kodim24_full](png/kodim24_full.png)

