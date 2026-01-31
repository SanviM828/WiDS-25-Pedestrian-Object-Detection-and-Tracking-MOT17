# Pedestrian Detection and Tracking (MOT17)
**Endterm Progress Submission: End-to-End Pipeline using YOLOv5 and BoT-SORT**

---

## Project Overview
This repository contains a complete pipeline for **Multi-Object Tracking (MOT)** in crowded environments. The project focuses on accurately detecting pedestrians and maintaining their identities across video frames using the **MOT17** benchmark dataset.

The project is divided into two phases:
1.  **Phase I (Detection):** Training a custom YOLOv5 model to localize pedestrians in crowded frames.
2.  **Phase II (Tracking):** Implementing a Multi-Object Tracking (MOT) pipeline using **BoT-SORT** to maintain identity persistence across frames.

## Repository Contents
This repository includes two versions of the project code for reference:
* **`wids_pdtaa_detection.ipynb`**: Contains the code for **Phase I only**. Use this if you want to replicate the object detection training and validation steps in isolation.
* **`wids_pdtaa_tracking.ipynb`**: Contains the complete, unified pipeline for **Phase I (Detection) and Phase II (Tracking)**. This is the final version of the project that generates the object tracking video output.
* **`Midterm_Report.pdf`**: The formal report detailing theoretical background, methodology, and comparative analysis.
* **`mot_op_filtered.avi`**: **(Final Output)** The optimized tracking video with class-filtering applied (pedestrians only).
* **`mot_og_op.avi`**: The initial raw tracking video showing the environmental noise challenges (e.g., furniture detection).

  
## Key Results

### Phase I: Object Detection
We successfully trained a custom object detector on the MOT17 benchmark dataset. Comparative analysis identified **Transfer Learning** as the optimal strategy.

| Model Variant | mAP@0.5 | Observation |
| :--- | :--- | :--- |
| **YOLOv5s** | 0.725 | Fast but lower accuracy on small/distant objects. |
| **YOLOv5m** | 0.760 | Improved accuracy due to deeper architecture. |
| **YOLOv5m-Frozen** | **0.773** | **Best Performance.** Achieved by freezing the COCO-pretrained backbone to prevent catastrophic forgetting. |

### Phase II: Multi-Object Tracking (MOT)
We integrated the custom `YOLOv5m-Frozen` weights with the **BoT-SORT** tracking algorithm.

* **Challenge:** Initial deployments revealed sensitivity to environmental noise (e.g., classifying furniture as objects) due to the underlying COCO pre-training.
* **Solution:** Implemented a **Post-Processing Class Filter** (`classes=[0]`) within the inference loop.
* **Outcome:** Successfully eliminated false positives, achieving robust pedestrian tracking with consistent ID assignment even during occlusions.

## Tech Stack
* **Platform:** Google Colab (Tesla T4 GPU)
* **Detection:** PyTorch (YOLOv5)
* **Tracking:** Ultralytics (BoT-SORT / DeepSORT)
* **Dataset:** MOT17 (Multiple Object Tracking Benchmark)
