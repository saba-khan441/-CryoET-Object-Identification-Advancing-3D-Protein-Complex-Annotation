### CZII - CryoET Object Identification

**Advancing 3D Protein Complex Annotation with Deep Learning**

#### 📌 Overview

Cryo-electron tomography (Cryo-ET) enables high-resolution 3D reconstructions of cellular structures, providing critical insights into molecular arrangements. However, identifying protein complexes remains a major challenge due to:

**1.High noise levels**

**2.Low contrast**

**3.Missing wedge artifacts in tomographic data**

This project introduces a YOLO-based deep learning model for detecting and localizing protein complexes in Cryo-ET images. The model leverages synthetic Cryo-ET data in Zarr format, applies advanced preprocessing techniques, and refines detection accuracy using k-d tree spatial structures.

#### 📂 Dataset Description

The dataset consists of 3D tomograms with ground truth annotations, designed to facilitate automated protein complex identification. The primary objective is to detect and predict particle centers in tomograms and submit predictions for five scored particle types.

#### 🧩 Particle Types & Difficulty Levels

**Easy:** apo-ferritin, ribosome, virus-like particle

**Hard:** beta-galactosidase, thyroglobulin

**Not scored:** beta-amylase (for reference but not included in evaluation)

#### Dataset download
click on link and download complete dataset

https://www.kaggle.com/competitions/czii-cryo-et-object-identification/data

#### 📁 Dataset Structure

**Train Data (train/)**

**Static Tomograms** (train/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/):

denoised.zarr/ → Contains tomographic data

Ground Truth (train/overlay/ExperimentRuns/{experiment}/Picks/):

{particle_type}.json → Contains particle coordinates

**Test Data (test/)**

**Static Tomograms** (test/static/ExperimentRuns/{experiment}/VoxelSpacing10.000/):

denoised.zarr/ → Contains tomographic data (without labels)

#### ⚙️ Installation

#### 🔽 Downloading and Archiving YOLO (Ultralytics) for Offline Use

!pip download -d ./packages ultralytics

!tar cfvz archive.tar.gz ./packages

#### 🔧 Installing YOLO (Ultralytics) Offline

!tar xfvz /kaggle/input/ultralytics-for-offline-install/archive.tar.gz

!pip install --no-index --find-links=./packages ultralytics

!rm -rf ./packages

#### 📦 Installing Required Dependencies

!cp -r '/kaggle/input/hengck-czii-cryo-et-01/wheel_file' '/kaggle/working/'

#### install asciitree and zarr from local wheels

!pip install /kaggle/working/wheel_file/asciitree-0.3.3/asciitree-0.3.3.whl

!pip install --no-index --find-links=/kaggle/working/wheel_file zarr

#### 🏗️ Model Details

**Model:** YOLO-based deep learning architecture

**Training Data:** Synthetic Cryo-ET dataset (best_synthetic.pt)

**Evaluation Metric:** Recall-weighted F-beta score (F-beta=4)

#### 🔄 Preprocessing & Post-processing

##### 🔬 Preprocessing Steps

Multi-slice extraction to enhance spatial features

Intensity normalization for uniform contrast

 Noise reduction to improve detection accuracy

##### 🛠️ Post-processing Steps

 k-d tree spatial structures for refining detection precision

 Confidence thresholding to reduce false positives

 Non-maximum suppression for better localization

#### 📊 Results

Achieved high recall and improved localization of protein complexes

Effective detection of macromolecular structures in noisy Cryo-ET data

 Post-processing with k-d trees significantly enhanced spatial accuracy

 ##### Submission format

![image](https://github.com/user-attachments/assets/f33fad58-7d2c-4a6f-9361-39bfa7ce309f)

##### Kaggle Scores (private and public)

![image](https://github.com/user-attachments/assets/e4d7eb32-bff0-4aca-b640-5c855e3b772b)



#### 🚀 Future Work

🔹 Fine-tuning the model on real Cryo-ET datasets

🔹 Hyperparameter optimization for improved detection performance

🔹 Enhanced post-processing techniques for better spatial precision

🔹 Integrating additional deep learning models for ensemble predictions













