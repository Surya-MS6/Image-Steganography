# Image Steganography

**Image hiding and recovery using Discrete Wavelet Transform (DWT) and Singular Value Decomposition (SVD).**

An image processing project that embeds a secret image into a cover image and reconstructs the hidden information through a decoding process. The implementation combines frequency-domain transformation, matrix decomposition and password validation.

---

## ◈ Project Overview

Image steganography is a technique for concealing information within a digital medium without making the embedded content immediately apparent.

This project implements image-to-image steganography using DWT and SVD. The cover and secret images are processed through their RGB channels, and the hidden image information is embedded into the singular values of the cover image.

The resulting steganographic image can be processed by the decoding procedure to recover the embedded image.

## ⚙️ Technical Approach

### Discrete Wavelet Transform (DWT)

DWT decomposes each RGB channel into four frequency components:

| Component | Description |
|---|---|
| `cA` | Approximation coefficients |
| `cH` | Horizontal detail coefficients |
| `cV` | Vertical detail coefficients |
| `cD` | Diagonal detail coefficients |

The implementation uses the **Daubechies 20 (`db20`) wavelet**. Approximation coefficients are used for SVD-based embedding, while the detail coefficients are retained for reconstruction.

### Singular Value Decomposition (SVD)

SVD decomposes the approximation coefficient matrices into their singular value components.

The embedding operation modifies the cover image's singular values using the secret image's singular values:

```python
Embedded_S = Cover_S + (0.1 * Secret_S)
```

The modified coefficients are reconstructed and passed through the inverse DWT to produce the steganographic image.

## ⇄ Encoding & Decoding

**Encoding**

```text
Cover Image ───────┐
                   ├── RGB Separation
Secret Image ──────┘
                         │
                         ▼
                    DWT Decomposition
                         │
                         ▼
                    SVD Decomposition
                         │
                         ▼
                   Singular Value
                      Embedding
                         │
                         ▼
                      Inverse DWT
                         │
                         ▼
                Steganographic Image
```

**Decoding**

```text
Steganographic Image
         │
         ▼
   Password Validation
         │
         ▼
   DWT Decomposition
         │
         ▼
   SVD Decomposition
         │
         ▼
    Information Extraction
         │
         ▼
     Image Reconstruction
         │
         ▼
      Hidden Image
```

## ✦ Implementation Details

| Component | Technology |
|---|---|
| Programming language | Python |
| Numerical computation | NumPy |
| Wavelet transformation | PyWavelets |
| Image processing | OpenCV |
| Image handling | Pillow |
| Visualization | Matplotlib |
| Wavelet | Daubechies 20 (`db20`) |
| Embedding factor | `0.1` |

## ▣ Supported Image Categories

The project configuration includes five categories:

| Category | Hidden Image |
|---|---|
| School | `pic1.jpg` |
| Hospital | `pic2.jpg` |
| Military Base | `pic3.jpg` |
| National Park | `pic4.jpg` |
| Armory | `pic5.jpg` |

Image paths and password information are maintained in `information.json`.

## ⌘ Installation & Execution

**Clone the repository**

```bash
git clone https://github.com/Surya-MS6/Image-Steganography.git
cd Image-Steganography
```

**Install dependencies**

```bash
pip install -r requirements.txt
```

**Run the application**

```bash
python project.py
```

Select an operation from the terminal:

| Input | Operation |
|---|---|
| `1` | Encode |
| `2` | Decode |
| `3` | Exit |

Run the application from the project root directory and make sure the required image files and configuration paths are available.

## ▤ Project Structure

```text
Image-Steganography/
│
├── project.py
├── information.json
├── requirements.txt
├── SETUP.md
├── README.md
├── LICENSE
├── .gitignore
│
├── Cover_Images/
│   ├── README.md
│   ├── pic20.jpg
│   ├── pic21.jpg
│   ├── pic22.jpg
│   ├── pic23.jpg
│   └── pic24.jpg
│
└── Hidden_Images/
    ├── README.md
    ├── pic1.jpg
    ├── pic2.jpg
    ├── pic3.jpg
    ├── pic4.jpg
    └── pic5.jpg
```

**Generated outputs:**
- `stegnographic.jpg` — Encoded steganographic image.
- `Hidden image.jpg` — Reconstructed hidden image.
