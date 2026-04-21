# C3D-dataset
A dataset used for real-time engineering cost estimation and prediction.




# Documentation for the C3D Dataset

## 1. Dataset Introduction and Core Features
The Customized Construction Cost Dataset (C3D for short) is a large-scale, multi-modal dataset specifically constructed for visual perception at construction sites, semantic mapping of Building Information Modeling (BIM), and cost analysis. The core objective of this dataset is to break the semantic barrier between traditional visual observation at construction sites and the cost control systems of BIM and Enterprise Resource Planning (ERP).

- **Data Scale and Source**: The data was collected from three large commercial building projects over a time span of 12 months. It includes a total of 45,000 frames of meticulously annotated 1080p high-definition construction site images.
- **Multi-modal Alignment**: The image data is strictly synchronized in terms of timestamps and spatial coordinates with the project's BIM model (compliant with the IFC standard) and the daily project control records based on the ERP system (i.e., Visually Observable Cost, VOC).

## 2. Data Annotation System and Modal Composition

- **Object Detection and Tracking Annotation**: It includes 2D bounding boxes and unique track IDs for key entities at the construction site (such as tower cranes, concrete mixer trucks, workers, and materials), supporting research on identity continuity across occlusions and over long periods.
- **BIM Semantic Mapping Anchor Points**: It provides mapping labels between visual targets and BIM entities. This subset has been strictly verified manually and includes visual trajectories, corresponding BIM anchor points, and correctness labels determined by a tripartite agreement, covering the following operational dimensions:
  - Static Structural Components: Directly mapped to physical entities such as beams, columns, and slabs.
  - Regional Personnel/Activities: Workers or construction activities are mapped to specific spaces (`IfcSpace`) or zones (`IfcZone`).
  - Temporary Equipment and Material Agents: Mapping of dynamically moving assets or delivery events during the construction process.
- **Cost Labels (VOC)**: All visually observable activities and entities are mapped to specific cost categories through a fixed semantic cross-border specification and aligned with the daily Visually Observable Cost (VOC) in the ERP system.

## 3. Dataset Partitioning
To ensure the rigor of dataset usage and the generalization ability of downstream models, the C3D dataset strictly abandons the traditional random shuffling strategy in data partitioning and adopts a strict time-series partitioning mechanism based on "site - month".

- **Training Set**: The earliest continuous time window data from each site is selected for model weight optimization and temporal feature learning.
- **Validation Set**: The continuous time window data after the training set is selected specifically for hyperparameter selection and threshold calibration.
- **Test Set**: The latest time window data from each site is selected for final performance evaluation.

## 4. Data Usage Declaration and Release Constraints
Since the C3D image data, BIM-related annotations, and VOC records derived from the ERP contain highly commercially sensitive information and privacy-constrained content, the complete end-to-end dataset cannot be publicly released without restrictions at present.
- Third-party verification and reproduction must be based on strictly controlled data access permissions.
- The anti-leakage evaluation protocol and multi-modal annotation paradigm established by the dataset provide a standardized auditing and testing paradigm for application-level evaluations in the future "BIM + Deep Learning" field.
