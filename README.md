# CV Assignment 1 - Multi-Instance Object Recognition in Cluttered Scenes

This project detects and localizes multiple instances of a template object inside a cluttered query scene, robust to scale, rotation, partial occlusion, and heavy background noise.

## Assignment Compliance Summary

Implemented from scratch:

1. Feature correspondence/matching
2. Euclidean descriptor distance calculation
3. Lowe ratio test
4. 4D generalized Hough transform hypothesis generation
5. Hough-space custom binning/clustering
6. Affine transformation estimation setup
7. Least-squares affine solving (`np.linalg.lstsq`)
8. RANSAC
9. Geometric verification
10. IoU calculation
# CV Assignment 1

## Overview
This submission implements a complete multi-instance object recognition pipeline for cluttered scenes. The system detects repeated occurrences of a template object in a query image while handling scale change, rotation, partial occlusion, and background clutter.

## Method Summary
The pipeline follows these steps:
1. Extract SIFT keypoints and descriptors from the template and query images.
2. Match descriptors with a custom Euclidean distance search and Lowe ratio test.
3. Convert matched pairs into 4D Hough hypotheses over center, scale, and rotation.
4. Cluster Hough votes to generate candidate object instances.
5. Verify each candidate with custom affine RANSAC and least-squares refinement.
6. Apply geometric sanity checks, project the template corners, and build bounding boxes.
7. Remove duplicate detections with manual IoU-based non-maximum suppression.
8. Repeat greedily to recover multiple objects from the same scene.

## Implementation Notes
- All matching, Hough voting, affine estimation, RANSAC, IoU, and NMS logic are implemented in the project code.
- OpenCV is used for image I/O, SIFT, and drawing utilities.
- The main configuration values live in `src/config.py`.

## Input and Output
- Input images: `data/template.jpeg` and `data/query.jpeg`
- Main entry point: `main.py`
- Result files: the `outputs/` folder contains the visualizations and summaries, including `statistics.json` and `statistics.txt`.

## Reproducibility
Run the project with:

```bash
pip install -r requirements.txt
python main.py
```

## Submission Checklist
- Source code is cleaned of inline comments and docstrings.
- README is rewritten as a compact assignment report.
- The configured input paths match the images in `data/`.
- Generated outputs are already organized under `outputs/`.
│
