Fine-tuning YOLOv8m-pose for Animal Pose Estimation (Macaques)
1. Project Context
Pose estimation, the task of predicting keypoint locations on living beings from images, is a fundamental problem in computer vision. While traditionally applied to humans, its application is expanding to animals to support fields like biomechanics, zoology, and ethology.

The advent of powerful pre-trained models like YOLOv8-pose allows for rapid adaptation of complex architectures to new datasets through fine-tuning.

2. Project Foundation: Model, Data, and Analytical Approach
This project is built upon three key components:

Model: YOLOv8m-pose, a lightweight and high-performance model designed for pose estimation.
Data: The MacaquePose dataset, containing annotated images of macaque monkeys with 17 bodily keypoints.
Fine-tuning: Specific training of the pre-trained model, adapted to the morphological characteristics of macaques.
To evaluate the effectiveness of our fine-tuning, two complementary analyses were conducted:

Quantitative Analysis: Using evaluation metrics (precision, recall, mAP50, mAP50-95), visualized over the 8 training epochs.
Qualitative Analysis: Through direct observation of predicted keypoints on images, allowing for visual validation of the model's performance.
These two aspects together form a comprehensive evaluation of the YOLOv8m-pose model applied to animal pose estimation.

3. Architecture and Adopted Approach
[Include the architecture diagram image here, e.g., ![Architecture Diagram](archi.png)]

Our practical work proceeded step-by-step:

4. Data Preparation and Exploration
Google Drive Mounting: Accessing the dataset stored on Google Drive.
Dataset Extraction: Unzipping the macaquepose_v1.zip file.
File Integrity Verification and Dataset Organization: Ensuring successful extraction and checking the structure of the unzipped data.
Dependency Installation: Installing Ultralytics and PyYAML.
Loading Annotations: Loading the annotations.csv file into a pandas DataFrame.
Exploratory Data Analysis (EDA)
Distribution of Valid/Invalid Images: Analyzing the number of images with complete vs. incomplete keypoints.
Bounding Box Dimension Histograms: Visualizing the distribution of bounding box widths and heights.
Image Quality Pie Chart: Assessing image quality based on the number of visible keypoints.
Missing Keypoints Barplot: Identifying keypoints that are most frequently missing.
Key Finding: A significant number of images had missing keypoints, indicating noisy or incomplete data that could impact model performance.

5. Data Cleaning and Subset Preparation
Objective: Create a clean data subset for training.

Approach: We built a subset named macaquepose_subset containing only images with all keypoints valid. This ensures high-quality learning without noise from incomplete or corrupted labels.

Steps:

Rigorous filtering of annotations.
Conversion of annotations to the YOLOv8 Pose format (56 values per line).
Organizing the dataset into a clear structure (images/, labels/, dataset.yaml) compatible with Ultralytics.
6. Annotation Visualization
Visualizing bounding boxes and keypoints on images from the clean subset to confirm the accuracy of the conversion.

7. Train/Validation Split
Splitting the data into 90% for training and 10% for validation.

8. Creating dataset.yaml
Generating the dataset.yaml file required by YOLOv8 Pose, containing paths to training and validation data, number of classes, and keypoint information.

9. YOLOv8 Pose Training
Objective: Fine-tune the YOLOv8m-pose model on the MacaquePose dataset.

Method: Training the model for 8 epochs, a strategic choice considering Google Colab's resource limitations while allowing for reasonable model convergence.

Observations:

Training losses (box, pose, kobj, cls, dfl) decreased progressively.
Precision, recall, and mAP metrics showed clear improvement.
10. Training Analysis
Plotting Losses: Visualizing the training loss curves over epochs.
Plotting Bounding Box Metrics: Tracking precision, recall, and mAP for bounding box detection.
Plotting Pose Metrics: Tracking precision, recall, and mAP for keypoint estimation.
Interpretation: The metrics demonstrated a consistent learning process and progressive stability. The high mAP50 for bounding boxes and promising mAP50 for pose estimation confirm the model's effective learning.

11. Qualitative Analysis through Predictions
Visualizing model predictions on validation images, showing correctly positioned keypoint skeletons and bounding boxes.

12. Prediction Statistics
Calculating and visualizing the average confidence of YOLOv8m-pose predictions on a sample of images.

Observation: Predictions generally showed high confidence (above 70%), with lower confidence in challenging cases (ambiguous poses, partial visibility, blur).

Conclusion
This project successfully demonstrated the effectiveness of fine-tuning YOLOv8m-pose for animal pose estimation using the MacaquePose dataset. Through rigorous data preparation, controlled training, and comprehensive quantitative and qualitative analysis, we achieved significant performance improvements in macaque pose estimation. This work serves as a foundation for future research on other species and more complex scenarios.



2/2

