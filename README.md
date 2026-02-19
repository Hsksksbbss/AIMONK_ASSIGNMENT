# AIMONK_ASSIGNMENT



  Problem Statement
This project addresses a multi-label image classification problem where each image can have multiple attributes. The dataset contains images along with 4 attribute labels per image. Some attribute values are marked as "NA", indicating missing information.



  Approach

 1. Model Selection
- Used **MobileNetV2** pretrained on **ImageNet**.
- Transfer learning was applied instead of training from scratch (as required).
- Final classification layer modified to output 4 attributes.
- Activation function: **Sigmoid** (for multi-label classification).

 2. Handling Missing Labels (NA)
- NA values were converted to `-1`.
- Implemented a **custom masked loss function** to ignore missing labels during training.
- Only valid labels (0 or 1) contribute to loss calculation.

 3. Loss Function
- Binary Cross Entropy (with masking for NA values).

 4. Training Details
- Input size: 224 × 224
- Optimizer: Adam
- Epochs: 5
- Batch size: 16


 Loss Curve
The training loss curve is included as `loss_curve.png`.



 Inference
An inference script is provided to:
- Load the trained model
- Predict attributes for a given image
- Print attributes with probability > 0.5



 Handling Imbalanced Data (Discussion)
The dataset appears imbalanced across attributes. Possible improvements include:
- Class weighting
- Focal loss
- Data augmentation
- Oversampling minority classes

Due to time constraints, imbalance handling techniques are discussed but not fully implemented.



 Files Included

- `train.ipynb` – Training code
- `final_model.h5` – Trained model weights
- `loss_curve.png` – Training loss visualization
- `labels.txt` – Dataset labels



 Conclusion
This solution uses transfer learning with proper handling of missing labels and multi-label classification strategy. The pipeline is modular and can be extended with validation, fine-tuning, and augmentation for further improvements.

