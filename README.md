# Star Pattern Matching for Constellation Detection

This project implements a star-matching system that\
identifies stars in astronomical images and compares them to a reference catalog using geometric pattern matching.

## Features

- **Star Detection** from images using OpenCV blob detection.
- **Triplet Matching** via geometric hashing (SPHT).
- **Orientation Validation** using Kabsch algorithm and RMS error.
- **Support for Confidence Scoring** and visual star alignment.

## Installation

1. Clone the repository.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Modify the `__main__` section in `algorithms.py` to load your own star images (e.g., images of constellations) and run the identification and matching pipeline.

Example images should be placed in the `Photos/` directory.

```python
img1 = "Photos/ursa-major-reduced.png"
img2 = "Photos/ursa-major-original.jpg"
```

The program will:

- Detect stars in both images.
- Build a hash table of star triplets from a reference catalog.
- Match the triplets and filter out uncertain matches.
- Draw lines between matched stars in both images with confidence color coding.

## Project Structure

- `algorithms.py`: Core algorithms (brute-force ID, SPHT matching, orientation validation)
- `helper_functions.py`: Utility functions for detection, SPHT generation, visualization, and math.
- `requirements.txt`: Python package dependencies.
- `bsc5-short.json`: Brightest stars in the visible sky catalog.
- `virgo_stars.json`: ~80 Stars in the virgo constellation.
- `Photos/`: Images read and used by the algorithms.
- `Detect/`: Proccessed images for referencing the detection points. 

## Notes

- Uses a subset of the Bright Star Catalog (BSC) stored as `bsc5-short.json`.
- Matching relies on geometric similarity between triangles formed by detected stars and catalog entries.
- Confidence scores are based on vote frequency from multiple matched triplets.
- Brute forcing the entire hashing of the catalog would take an elongated time. The code samples hard coded values for the Ursa Major and Vigro for demonstration purposes.

## License

MIT License.

