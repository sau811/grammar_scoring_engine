# Grammar Score Prediction from Audio

## Introduction

This project addresses the task of predicting grammar proficiency from audio recordings of spoken language. By extracting relevant acoustic features from the speech, this system uses machine learning models to estimate grammatical competence. This approach has significant applications in fields like language education, speech therapy, and the development of automated language assessment tools. The goal is to provide a reliable method for evaluating grammar, enabling real-time feedback for learners and assisting clinicians in tracking progress.

## Project Overview

The project follows a systematic approach with the following stages:

### 1. **Audio Feature Extraction**
   The primary task is to extract relevant acoustic features from the audio files. These features are critical for understanding the speaker's speech patterns. The **Librosa** library is used to extract:
   
   - **Mel-Frequency Cepstral Coefficients (MFCCs)**: Represent the short-term power spectrum of the audio, essential for capturing speech features.
   - **Zero-Crossing Rate (ZCR)**: Measures the frequency at which the audio signal crosses zero, providing an indication of the noisiness or frequency of the signal.
   - **Spectral Centroid**: Describes the "center of mass" of the frequency spectrum, helping to characterize the speech's harmonic content.
   - **Spectral Bandwidth**: Measures the spread of frequencies around the spectral centroid.
   - **Root Mean Square (RMS) Energy**: Represents the loudness or overall energy of the signal.

   These features enable the machine learning model to analyze various aspects of the speaker's voice that are important for grammar scoring.

### 2. **Machine Learning Model**
   A **Random Forest Regressor** is employed to predict grammar scores based on the extracted audio features. Random Forest is an ensemble learning method that builds multiple decision trees, aggregating their predictions to improve accuracy. It is especially effective for:
   - Handling non-linear relationships in the data.
   - Mitigating the risk of overfitting.
   - Managing outliers in the dataset.

   This model takes the acoustic features as input and outputs a prediction of grammar proficiency, trained on a dataset with labeled grammar scores.

### 3. **Data Handling**
   The **Pandas** library is used to manage and process the dataset. The data is organized into a **DataFrame**, which facilitates efficient manipulation, filtering, and transformation of the data. Pandas ensures the integrity and quality of the data by handling tasks such as:
   - Merging datasets.
   - Dealing with missing values.
   - Performing statistical analysis.

   Organizing the data correctly is crucial for successful model training and prediction.

### 4. **Process Automation**
   This project automates the entire process of feature extraction and model prediction. By automating these steps, the project reduces the potential for human error and ensures that large volumes of audio data can be processed efficiently. This automation enables:
   - Faster and more objective grammar evaluations.
   - Scalability to handle large datasets.

## System Requirements

To run this project, you need the following Python libraries:

- **Librosa**: For extracting audio features.
- **NumPy**: For numerical operations.
- **Pandas**: For data manipulation and analysis.
- **Scikit-learn**: For building and training the machine learning model.
- **TQDM**: For providing progress bars during long-running tasks.

You can install the required libraries using:

```bash
pip install librosa numpy pandas scikit-learn tqdm
```

## Data Preparation

Before running the script, ensure the following:

1. **Audio Files**: Store the audio files in a directory. Ensure the filenames in the CSV file match exactly with the filenames of the audio files.
2. **CSV File**: This file should have two columns:
   - **Filenames**: The names of the audio files (without full paths).
   - **Grammar Scores**: Corresponding numeric grammar scores for each audio file.

Ensure the CSV is properly formatted for the script to function correctly.

## Script Execution

To run the script, follow these steps:

1. **Prepare the Data**: Place the audio files and CSV in the same directory.
2. **Run the Script**:
   Execute the Python script using:

   ```bash
   python grammar_scoring_script.py
   ```

   The script will perform the following steps:
   - Extract features from the audio files.
   - Load the pre-trained Random Forest Regressor model.
   - Predict grammar scores based on the extracted features.
   - Save the predictions in a CSV file.

3. **Output**: The script will generate a CSV file containing the predicted grammar scores for the audio files.
