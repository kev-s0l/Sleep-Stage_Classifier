## Sleep-Stage-Interpreter
This script processes EEG data in EDF format to classify infant sleep stages based on Delta and Theta band power. It uses the MNE-Python library for signal processing, filtering, and artifact rejection. The output is a sleep stage hypnogram plotted over time.

## Features 
- Loads EEG data from an EDF file.
- Selects key EEG channels (F4:M1, F3:M2, C4:M1, C3:M2, O2:M1, O1:M2).
- Band-pass filters signals (0.5–13 Hz).
- Applies Independent Component Analysis (ICA) for artifact rejection.
- Computes Delta (0.5–3 Hz) and Theta (4–8 Hz) power using Welch’s method.
- Classifies infant sleep stages per 30-second segment:
      - Wake (1)
      - N1 (2) – Transitional/drowsy sleep
      - N2 (3) – Light sleep
      - N3 (4) – Deep sleep (Quiet sleep)
      - REM (5) – Active sleep

- Generates a hypnogram-style plot of sleep stages across time.

## Requirements
- Make sure you have the following Python libraries installed:

      pip install mne numpy matplotlib

## Usage
1. Place your EEG .edf file in the working directory.
2. Update the script with the correct file path:

    edf_file_path = "YourData.edf"

3. Run the script:

    python infant_sleep_stages.py

4. A hypnogram plot will be generated showing sleep stage transitions over time

## Notes
- If a selected EEG channel is missing in the EDF file, the script automatically ignores it.
- ICA may fail for very short recordings or unusual data; in that case, the script skips ICA gracefully.
- The classification thresholds (1.5x ratios between Delta and Theta power) are simplified rules and may need refinement for real-world datasets.
- This script is designed with infant sleep EEG characteristics in mind.










  
