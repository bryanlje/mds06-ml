# 🏸 High-Speed Badminton Match AI Analyser (ML Research & Development)

![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![YOLOv11](https://img.shields.io/badge/-YOLOv11-blue?style=for-the-badge)

This repository serves as the **research lab and archive** for the High-Speed Badminton Match AI Analyser. It contains the raw notebooks used for data preparation, model experimentation, and training.

## ⚠️ Notice

**Please note:** The notebooks in this repository are **raw research artifacts**.
* **Code State:** Many notebooks are messy and may contain non-working code, debug blocks, or hardcoded paths specific to the original environment, which include Google Colab, Google Drive, and H100 servers (via RunAI).
* **Version Uncertainty:** As this project evolved rapidly, it is not able to determine which specific notebook version produced the final production weights.
* **Purpose:** These files are provided for transparency and reference regarding the development methodology, rather than as a clean, execute-from-top-to-bottom tutorial.

For the clean, production-ready inference pipeline, please refer to the **Backend API** repository linked below.

---

## 🔗 Project Structure & Repositories

This project is divided into three main repositories to handle the frontend, backend logic, and model development separately:

* **Frontend:** [https://github.com/bryanlje/mds06-frontend](https://github.com/bryanlje/mds06-frontend)
* **Backend API:** [https://github.com/bryanlje/mds06-backend](https://github.com/bryanlje/mds06-backend)
* **Model Training & Data Preparation (This Repo):** [https://github.com/bryanlje/mds06-ml](https://github.com/bryanlje/mds06-ml)

---

## 📂 Repository Content

### 1. Final Pipeline (`00_final_pipeline/`)
* **`FINAL_FULL_PIPELINE.ipynb`**: The most complete integration notebook used to prototype the end-to-end logic (Detection → Tracking → Shuttle → Action) before it was refactored into the production backend.

### 2. Data Preparation (`01_data_preparation/`)
Scripts used to transform raw annotations into training datasets.
* `cvat_to_csv_bryan.ipynb`: Converting raw CVAT export JSONs into standardised CSV formats.
* `generate_clips_from_csv_bryan.ipynb`: Slicing full match videos into action-specific clips.
* `new_dataset_format.ipynb`: Formatting data for PyTorchVideo loaders.

### 3. Model Training & Experiments (`02_training_experiments/`)

#### **A. Player Detection (YOLO)**
Notebooks for training **YOLOv8/11** to detect players.
* `yolo_bryan training my_yolo11s_finals.ipynb` (Final training run).

#### **B. Player Tracking (StrongSORT + ReID)**
Experiments with **StrongSORT** and **OSNet** for player Re-Identification.

#### **C. Action Recognition (SlowFast)**
Extensive experimentation with **SlowFast (ResNet-101)** for classifying badminton shots.
* **Note on Training Process:** The training for the final SlowFast model was **highly iterative** and is not fully captured by a single notebook. It involved:
    * Many stop-start cycles.
    * Manually adjusting learning rates and epochs based on interim results.
    * Swapping datasets (high and standard frame rate clips) mid-training to refine performance.
    * *Therefore, the notebooks here represent snapshots of this process, with NO exact uninterrupted training run.*

### 4. Miscellaneous Research (`03_misc_research/`)
Exploratory work including DINOv3 foundation models and pose estimation tests.

### ❌ Missing Components
Please be aware that the following notebooks are not included in this archive:
1.  **1D CNN Training:** The training script for the contact detection model (Shuttlecock trajectory analysis).
2.  **Visualisation:** The standalone notebook used for generating charts to showcase our results (bar charts, heatmaps, etc).

---

## 👥 Team

This project was developed by **Team MDS06**:

* **Bryan Leong Jing Ern**
* **Phua Yee Yen**
* **Ting Shu Hui**
* **Lee Jian Jun Thomas**

---

## 📧 Contact

Email: [2025mds06@gmail.com](mailto:2025mds06@gmail.com)

Project Link: [https://github.com/bryanlje/mds06-frontend](https://github.com/bryanlje/mds06-frontend)
