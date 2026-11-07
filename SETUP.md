# Setup Guide

This guide explains how to configure and run the Image Steganography project locally.

## Project Requirements

- Python 3.x
- Required Python libraries
- Cover and hidden image files

## Project Folder Organisation

Keep the project files arranged as follows:

```text
Image-Steganography/
│
├── Cover_Images/
│   ├── pic20.jpg
│   ├── pic21.jpg
│   ├── pic22.jpg
│   ├── pic23.jpg
│   └── pic24.jpg
│
├── Hidden_Images/
│   ├── pic1.jpg
│   ├── pic2.jpg
│   ├── pic3.jpg
│   ├── pic4.jpg
│   └── pic5.jpg
│
├── project.py
├── information.json
├── README.md
├── SETUP.md
├── LICENSE
└── .gitignore
```

## Install Dependencies

Install the required Python libraries using:

```bash
pip install numpy PyWavelets matplotlib opencv-python Pillow
```

## Configure Image Paths

The `information.json` file stores the image paths and password information for each category.

Example:

```json
{
    "school": {
        "Image_to_Hide": "Hidden_Images/pic1.jpg",
        "Image_to_Send": "Cover_Images/pic21.jpg",
        "Password": "student"
    }
}
```

The configuration includes five categories:

- School
- Hospital
- Military Base
- National Park
- Armory

Make sure the image paths match the actual folder structure.

## Run the Application

Open a terminal in the project root directory and execute:

```bash
python project.py
```

The program provides three options:

| Input | Operation |
|---|---|
| `1` | Encode an image |
| `2` | Decode a hidden image |
| `3` | Exit |

### Encoding

1. Select the image category.
2. Provide the path of the cover image.

   Example: `Cover_Images/pic21.jpg`

3. The program processes the images and generates the steganographic image.

### Decoding

1. Select the corresponding image category.
2. Enter the configured password when prompted.
3. The program performs the extraction and displays the recovered image.

## Important Notes

- Keep `project.py`, `information.json` and both image folders in the project root directory.
- Ensure all configured image paths are valid.
- The selected cover image is resized to match the hidden image dimensions. The current implementation saves the resized image to the original cover image path.
- The decoding process requires the corresponding image configuration and password.

---
**Project:** Image Steganography  
**Techniques:** Discrete Wavelet Transform (DWT) and Singular Value Decomposition (SVD)
