# Coin Detection using OpenCV

This repository contains a computer vision project for detecting and counting coins in an image using the **OpenCV** library in Python. The project explores two distinct segmentation and detection methodologies: the **Watershed Algorithm** and the **SimpleBlobDetector**.

-----

## Getting Started

These instructions will get you a copy of the project up and running on your local machine.

### Prerequisites

You need **Python 3.x** installed. The core dependencies can be installed using `pip`.

```bash
pip install opencv-python numpy matplotlib jupyter
```

### File Structure

The main logic and steps are contained within the Jupyter Notebook.

```
Coin-Detection-OpenCV/
├── Coin-Detection.ipynb      # Main Jupyter Notebook with all the code
└── CoinsA.png                # Sample input image
└── README.md                 # This file
```

-----

## Methodologies

The project demonstrates two different approaches to coin detection, each suitable for varying image conditions.

### 1\. Watershed Algorithm

The Watershed algorithm treats the image as a topographic map, where pixels' intensity values represent height. It is particularly effective for separating **touching or overlapping objects** (coins).

**Key Steps:**

1.  **Grayscale & Thresholding:** Convert to grayscale and apply **OTSU's binarization**.
2.  **Morphological Operations:** Use **Opening** for noise removal, and **Dilation** to identify the **sure background**.
3.  **Distance Transform:** Apply the distance transform and thresholding to find the **sure foreground** (centers of the coins).
4.  **Marker Generation:** Create markers identifying the sure foreground, sure background, and the **unknown region**.
5.  **Watershed Application:** Apply the algorithm to segment the coins, with boundaries marked in a distinct color (e.g., red).

### 2\. SimpleBlobDetector

This method is an easier, parameter-driven approach to finding circular objects (blobs) in an image. It relies on pre-defined criteria to isolate the coins.

**Key Parameters Used:**

  * `filterByArea`: Filters blobs based on size (e.g., `minArea = 500`).
  * `filterByCircularity`: Filters for shapes close to a perfect circle (e.g., `minCircularity = 0.8`).
  * `filterByConvexity`: Filters for convex shapes (e.g., `minConvexity = 0.8`).
  * `filterByInertiaRatio`: Filters for how close the shape is to a circle.

-----

## Usage

To run the project, simply launch the Jupyter Notebook and execute the cells sequentially.

1.  **Start Jupyter:**
    ```
    jupyter notebook
    ```
2.  Open the `Coin-Detection.ipynb` file.
3.  Run all cells to see the results for both detection methods.

### Expected Output

The notebook will display intermediate processing steps (threshold, distance transform) and two final output images:

1.  An image showing the coins segmented and their boundaries highlighted by the **Watershed Algorithm**.
2.  An image with circles drawn around the centers of the coins detected by the **SimpleBlobDetector**, along with a printout of the total **number of coins detected**.

-----

*Developed as a class activity for **Morphological Operators** and **Object Detection** in Computer Vision.*
