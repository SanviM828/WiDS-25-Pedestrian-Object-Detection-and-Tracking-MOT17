# WiDS-25-Pedestrian-Anomaly-Detection-MOT17
Midterm project for Unsupervised Anomaly Detection using YOLOv5 on the MOT17 dataset.

# Pedestrian Detection and Tracking for Anomaly Analysis
**Midterm Progress Submission**

---

## Project Overview
This repository contains the code and documentation for the midterm phase of the "Unsupervised Anomaly Detection" project. The objective is to detect and track pedestrians in crowded environments to identify abnormal behaviors (e.g., sudden running, dispersal).

## Repository Contents
* **`Pedestrian_Detection_YOLOv5.ipynb`**: The complete training pipeline executed on Google Colab. It includes:
    * Data downloading (MOT17 Dataset).
    * Preprocessing (Converting annotations to YOLO format).
    * Training scripts for YOLOv5s, YOLOv5m, and Frozen-YOLOv5m.
* **`Midterm_Report_Sanvi_Majare.pdf`**: The formal report detailing theoretical background, methodology, and comparative analysis.

## Key Results (Midterm)
We successfully trained a custom object detector on the MOT17 benchmark dataset.

| Model Variant | mAP@0.5 | Observation |
| :--- | :--- | :--- |
| **YOLOv5s** | 0.725 | Fast but lower accuracy on small objects. |
| **YOLOv5m** | 0.760 | Improved accuracy. |
| **YOLOv5m-Frozen** | **0.773** | **Best Performance.** Achieved via transfer learning by freezing the backbone layers. |

## Tech Stack
* **Platform:** Google Colab (Tesla T4 GPU)
* **Framework:** PyTorch (YOLOv5)
* **Dataset:** MOT17 (Multiple Object Tracking Benchmark)

## Next Steps (Post-Midterm)
* Integration with **DeepSORT** for ID tracking.
* Implementation of velocity vector analysis.
* Development of the anomaly rule engine.
