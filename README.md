# COVID-ICU-Predictions
MOTIVATION
The COVID-19 pandemic has shown us the unpreparedness of our current healthcare system and services. We need to optimize the allocation of medical resources to maximize the utilization of resources. I have prepared this Machine Learning model based on the clinical data of patients admitted to the Hospital Sírio-Libanês, São Paulo and Brasilia. This will help us to predict the need of ICU for a patient in advance. With this information hospitals can plan the flow of operations and make critical decisions like shifting a patient to another hospital or determining the arrangement of resources within the time so that patients’ lives can be saved.

ABOUT THE DATASET
The dataset contains 1925 rows and 231 columns of anonymized patient data with 54 features: 
  Patient Demographics (3 features): Age above 65 years old, Age percentile, Gender
  Disease Groupings (9 features): Groupings 1-6 (past comorbidities), Hypertension, Immunocompromised, and Other
  Blood Test Results (36 features):
      Each with the following features:
        Mean
        Median
        Minimum
        Maximum
        Difference (max - min)
  Vital Signs Results (6 features): Diastolic blood pressure, Systolic blood pressure, Heart rate, Respiratory rate, Temperature, Oxygen
  saturation
      Each with the following features:
        Mean
        Median
        Minimum
        Maximum
        Difference (max - min)
        Relative difference (diff / med)

Patient data is aggregated by 5 time windows: 0-2, 2-4, 4-6, 6-12, and above 12 hours with indications of if the patient was admitted into ICU during that particular window (ICU column 0 = no, 1 = yes). The dataset contains float, integer, and object data types.

Patients are anonymized by a unique identifier PATIENT_VISIT_IDENTIFIER. There are 385 unique patients, each having 5 entries for the 5 time windows.

Some lab test and vital sign data is not available for all time windows, resulting in null or NaN (not a number) values. Missing values are handled by filling in the lab test and vital sign results with values from neighboring windows (previous or next entries) of the same patient based on availability (forward and backward fills).

AGE_PERCENTIL and WINDOW columns are non-numeric, so they will be transformed or normalized by encoding with numerical values between 0 and 1. 

OBJECTIVE
The objective of this study is to predict whether a patient will need to be admitted into the ICU based on their health information. So for the model to make more clinically relevant predictions, it will receive data only from the first window time frame of 0-2 hours and then from all windows except the last, above 12 hours. The earlier the model can predict the need for ICU treatment of the patient, the more it becomes clinically relevant.
