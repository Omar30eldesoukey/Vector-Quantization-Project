# Vector Quantization Image Compression

**Author:** Omar Eldesoukey (202202155)

---

## Overview
This project implements image compression using vector quantization (VQ) in both RGB and YUV color spaces. The YUV pipeline uses chroma subsampling (4:2:0) for improved compression. The project compares both methods quantitatively (PSNR, compression ratio) and visually.

---

## Directory Structure
```
VQImageCompression/
├── data/
│   ├── train/         # Training images (by domain)
│   └── test/          # Test images (by domain)
├── output/
│   ├── decompressed/      # RGB pipeline results
│   └── decompressed_yuv/  # YUV pipeline results
├── src/vq/
│   ├── Main.java
│   ├── ImageUtils.java
│   ├── VectorQuantizer.java
│   └── VQEncoderDecoder.java
├── resize_images.py       # Python script to resize images
├── requirements.txt       # Python dependencies
├── VQ_Report_OmarEldesoukey_202202155.tex   # LaTeX report
└── README.md
```

---

## How to Run

### 1. Prepare Data
- Place training images in `data/train/<domain>/` (e.g., `animal`, `face`, `nature`).
- Place test images in `data/test/<domain>/`.
- Use `resize_images.py` to resize all images to 128x128 for optimal performance:
  ```bash
  python resize_images.py
  ```

### 2. Compile Java Code
From the `src` directory:
```bash
javac -d ../bin vq/*.java
```

### 3. Run Compression Pipelines
From the `src` directory:
```bash
java -cp ../bin vq.Main
```
- This will run both the RGB and YUV pipelines, save decompressed images, and print PSNR and compression ratio for each image.

### 4. View Results
- Quantitative: Check the terminal output for PSNR and compression ratio for each image and method.
- Visual: Compare images in `output/decompressed/` (RGB) and `output/decompressed_yuv/` (YUV).

### 5. Report
- The LaTeX report (`VQ_Report_OmarEldesoukey_202202155.tex`) summarizes results, comparison, and code.
- You can compile it with Overleaf or a local LaTeX installation.

---

## Dependencies
- **Java JDK** (for main code)
- **Python 3** (for image resizing)
- **Pillow** (install with `pip install Pillow`)

---

## Key Files
- `src/vq/Main.java` — Main pipeline logic (RGB and YUV)
- `src/vq/ImageUtils.java` — Image utilities, color conversion, subsampling
- `src/vq/VectorQuantizer.java` — k-means clustering for codebook generation
- `src/vq/VQEncoderDecoder.java` — Vector extraction, compression, decompression
- `resize_images.py` — Batch resize images to 128x128

---

## Notes
- The YUV pipeline uses 4:2:0 subsampling: U and V channels are downsampled by 2 in each dimension.
- Compression ratio is higher for YUV, with only a small loss in PSNR compared to RGB.
- Results and code are summarized in the provided LaTeX report.

---

## Contact
For questions or improvements, contact Omar Eldesoukey.
