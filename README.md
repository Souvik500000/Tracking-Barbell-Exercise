# Context-Aware Applications for Strength Training

## Overview
This repository explores the possibilities of context-aware applications for strength training using machine learning. The project analyzes wristband accelerometer and gyroscope data to track exercises, count repetitions, and detect improper form. The goal is to develop models that can function as digital personal trainers.

## Motivation
Wearable fitness technology has significantly advanced in tracking aerobic exercises but remains underdeveloped for free weight exercises. This project investigates how machine learning can bridge this gap by enabling real-time tracking and feedback for strength training movements.

## Experimental Setup
### Data Collection
- **Participants**: 5 individuals performed barbell exercises.
- **Exercises Tracked**: Bench Press, Deadlift, Overhead Press, Row, Squat.
- **Repetitions & Sets**: Each participant performed 3 sets of 5 reps (heavy) and 3 sets of 10 reps (medium).
- **Equipment Used**: MbientLab's wristband sensor research kit.
- **Sensors**: Accelerometer (12.5Hz) and Gyroscope (25Hz).
- **Rest Period Data**: Captured to study state transitions from rest to exercise.

### Data Processing
- **Raw Data Size**: 69,677 entries containing timestamps and x, y, z values from the sensors.
- **Aggregation**: Time-step of 0.20s applied to minimize data loss.
- **Feature Engineering**:
  - Low-pass filtering to remove noise.
  - Principal Component Analysis (PCA) to reduce dimensionality.
  - Fourier transformation for frequency domain features.
  - Aggregated features like standard deviation and mean over 4s windows.
  - K-means clustering (k=4) to group exercises.

## Machine Learning Models
### 1. Exercise Classification
- **Algorithm**: Random Forest
- **Feature Selection**: Top 15 features selected using forward feature selection.
- **Regularization**: Optimized to prevent overfitting.
- **Results**:
  - Accuracy: **98.51%**
  - Precision, Recall, F1-score: High across all classes
  - Misclassification: Minor confusion between Bench Press & Overhead Press, and Deadlift & Row due to similar movement patterns.

### 2. Repetition Counting
- **Method**: Peak detection on scalar magnitude acceleration data.
- **Performance**:
  - Applied a strong low-pass filter (cut-off: 0.4Hz).
  - Error rate: **5%**
  - Adjusted method for each exercise for higher accuracy.

### 3. Form Detection
- **Algorithm**: Random Forest
- **Dataset**: Additional data collected for incorrect Bench Press execution.
- **Misclassified Forms**:
  - Lowering the bar too high on the chest.
  - Not touching the chest.
- **Results**: Accuracy of **98.53%** in detecting improper form.

## Generalization Challenges
- **Different Weight Classes**:
  - When trained on heavy weight data, accuracy dropped to **79.97%** on medium weight sets.
  - Similarly, training on medium weight resulted in **79.51%** accuracy on heavy sets.
- **Participant Variability**:
  - Leave-one-out cross-validation resulted in an average accuracy of **85.43%**.
  - Indicates the need for a larger dataset to improve generalization.

## Conclusion
This study demonstrates that machine learning can effectively track strength training exercises with high accuracy. However, generalization remains a challenge, requiring extensive training data across diverse users. Future work should focus on:
- Enhancing dataset diversity (age, skill levels, training styles).
- Expanding form analysis to other exercises.
- Integrating real-time feedback mechanisms for live workout correction.

## References
For detailed methodology, please refer to the full paper: "Exploring the Possibilities of Context-Aware Applications for Strength Training" by Dave Ebbelaar, Vrije Universiteit, Amsterdam.


---

## Setup Instructions

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/Souvik500000/Tracking-Barbell-exercise.git
   cd Tracking-Barbell-exercise
   ```

2. **Install Dependencies**  
   Install required Python libraries:  
   ```bash
   pip install -r requirements.txt
   ```

3. **Prepare Data**  
   - Place raw sensor data in the `data/raw` directory.  
   - Use the provided scripts in `scripts/` for data preprocessing and feature extraction.

4. **Run Classification Model**  
   Execute the main classification script:  
   ```bash
   python classify_exercises.py
   ```

5. **Run Repetition Counter**  
   Count repetitions for specific exercises:  
   ```bash
   python count_reps.py
   ```

6. **Form Detection**  
   Evaluate form detection with:  
   ```bash
   python detect_form.py
   ```

---

