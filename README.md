# Tracking Barbell Exercises

## Description
This project explores the development of a context-aware application for tracking barbell exercises. Using data collected from wristband sensors (accelerometer and gyroscope), the system aims to replicate the functionality of a personal trainer by:
- Classifying exercises
- Counting repetitions
- Detecting improper form

It employs machine learning techniques to analyze data from strength training sessions, focusing on core barbell exercises and leveraging supervised learning for high accuracy.

---

## Features
- **Exercise Classification**: Identifies exercises such as Bench Press, Squat, Deadlift, Overhead Press, and Row with 98.51% accuracy.  
- **Repetition Counting**: Counts repetitions with a simple peak-counting algorithm, achieving ~95% accuracy.  
- **Form Detection**: Detects improper bench press form (e.g., bar position errors) with 98.53% accuracy.  
- **Versatile Data Collection**: Supports medium and heavy weight classes, with realistic workout data.

---

## Technologies Used
- **Programming Language**: Python  
- **Machine Learning Models**: Random Forest, Neural Networks, SVM, etc.  
- **Data Processing**: Low-pass filtering, PCA, and feature engineering  
- **Hardware**: MbientLab’s wristband sensors for accelerometer and gyroscope data

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

## Data Collection
- Data was collected from 5 participants performing barbell exercises under realistic conditions.  
- The dataset includes acceleration and gyroscope readings recorded at high frequency (12.5 Hz and 25 Hz, respectively).

---

## Key Results
- Exercise classification achieved an accuracy of **98.51%**.  
- Repetition counting error rate was around **5%**.  
- Bench press form detection reached **98.53% accuracy**.

---

## Future Work
- Incorporate data from additional participants to improve model generalization.  
- Extend form detection to other exercises.  
- Explore real-time implementation on wearable devices.

---

## Contributors
- **Souvik Chakraborty**  
- Original Research by Dave Ebbelaar, Vrije Universiteit, Amsterdam.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
