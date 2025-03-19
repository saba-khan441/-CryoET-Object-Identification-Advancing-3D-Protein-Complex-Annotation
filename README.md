CZII - CryoET Object Identification

Advancing 3D Protein Complex Annotation with Deep Learning

📌 Overview

Cryo-electron tomography (Cryo-ET) enables high-resolution 3D reconstructions of cellular structures, providing critical insights into molecular arrangements. However, identifying protein complexes remains a major challenge due to:

High noise levels

Low contrast

Missing wedge artifacts in tomographic data

This project introduces a YOLO-based deep learning model for detecting and localizing protein complexes in Cryo-ET images. The model leverages synthetic Cryo-ET data in Zarr format, applies advanced preprocessing techniques, and refines detection accuracy using k-d tree spatial structures.

📂 Dataset Description

The dataset consists of 3D tomograms with ground truth annotations, designed to facilitate automated protein complex identification. The primary objective is to detect and predict particle centers in tomograms and submit predictions for five scored particle types.

🧩 Particle Types & Difficulty Levels

✅ Easy: apo-ferritin, ribosome, virus-like particle

⚠️ Hard: beta-galactosidase, thyroglobulin

❌ Not scored: beta-amylase (for reference but not included in evaluation)

📁 Dataset Structure

Train Data (train/)

🔹 Static Tomograms (train/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/):

denoised.zarr/ → Contains tomographic data🔹 Ground Truth (train/overlay/ExperimentRuns/{experiment}/Picks/):

{particle_type}.json → Contains particle coordinates

Test Data (test/)

🔹 Static Tomograms (test/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/):

denoised.zarr/ → Contains tomographic data (without labels)

⚙️ Installation

🔽 Downloading and Archiving YOLO (Ultralytics) for Offline Use

!pip download -d ./packages ultralytics
!tar cfvz archive.tar.gz ./packages

🔧 Installing YOLO (Ultralytics) Offline

!tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz
!pip install --no-index --find-links=./packages ultralytics
!rm -rf ./packages

📦 Installing Required Dependencies

!cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/'

# Install asciitree and zarr from local wheels
!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl
!pip install --no-index --find-links=/kaggle/working/wheel_file zarr

🏗️ Model Details

Model: YOLO-based deep learning architecture

Training Data: Synthetic Cryo-ET dataset (best_synthetic.pt)

Evaluation Metric: Recall-weighted F-beta score (F-beta=4)

🔄 Preprocessing & Post-processing

🔬 Preprocessing Steps

✔️ Multi-slice extraction to enhance spatial features✔️ Intensity normalization for uniform contrast✔️ Noise reduction to improve detection accuracy

🛠️ Post-processing Steps

✔️ k-d tree spatial structures for refining detection precision✔️ Confidence thresholding to reduce false positives✔️ Non-maximum suppression for better localization

📊 Results

✅ Achieved high recall and improved localization of protein complexes✅ Effective detection of macromolecular structures in noisy Cryo-ET data✅ Post-processing with k-d trees significantly enhanced spatial accuracy

🚀 Future Work

🔹 Fine-tuning the model on real Cryo-ET datasets🔹 Hyperparameter optimization for improved detection performance🔹 Enhanced post-processing techniques for better spatial precision🔹 Integrating additional deep learning models for ensemble predictions

























## CZII - CryoET Object Identification

**Advancing 3D Protein Complex Annotation with Deep Learning**

### Overview
Cryo-electron tomography (Cryo-ET) enables high-resolution 3D reconstructions of cellular structures, providing critical insights into molecular arrangements.

However, identifying protein complexes remains challenging due to high noise, low contrast, and missing wedge artifacts.

This project introduces a YOLO-based deep learning model for detecting protein complexes in Cryo-ET images.

We utilize synthetic Cryo-ET data stored in Zarr format, apply preprocessing techniques, and refine detection with k-d tree spatial structures.

### Dataset Description
The dataset consists of 3D tomograms and their corresponding ground truth annotations. 

The goal is to identify particle centers in tomograms and submit predictions for five scored particle types:

#### Particle Types & Difficulty Levels

✅ Easy: apo-ferritin, ribosome, virus-like-particle

✅ Hard: beta-galactosidase, thyroglobulin

❌ Not scored: beta-amylase

### Dataset Structure

Train Data (train/)

Static Tomograms (train/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/)

denoised.zarr/ → Contains tomographic data

Ground Truth (train/overlay/ExperimentRuns/{experiment}/Picks/)

{particle_type}.json → Contains particle coordinates

Test Data (test/)

Static Tomograms (test/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/)

denoised.zarr/ → Contains tomographic data (without labels)

### Installation

**Install ultralytics (YOLO) Offline**

!tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz

!pip install --no-index --find-links=./packages ultralytics

!rm -rf ./packages

**Install Required Dependencies**

!cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/'

## Install asciitree and zarr from local wheels

!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl

!pip install --no-index --find-links=/kaggle/working/wheel_file zarr

### Model Details

Model: YOLO-based deep learning model

Training Data: Synthetic Cryo-ET dataset (best_synthetic.pt)

Evaluation Metric: Recall-weighted F-beta score (F-beta=4)

### Preprocessing & Post-processing
**Preprocessing:**

Multi-slice extraction
Intensity normalization
Noise reduction

**Post-processing:**

k-d tree spatial structures for refining detection accuracy

### Results

High recall and improved localization of protein complexes

Effective detection of macromolecular structures in noisy Cryo-ET data

Post-processing with k-d trees enhances spatial accuracy

![image](https://github.com/user-attachments/assets/f33fad58-7d2c-4a6f-9361-39bfa7ce309f)


### Future Work

Fine-tuning on real Cryo-ET data

Hyperparameter optimization

Improved post-processing for enhanced detection







