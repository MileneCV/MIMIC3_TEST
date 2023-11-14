# Predict Hospital Mortality
The original data is from MIMIC3 - Multiparameter Intelligent Monitoring in Intensive Care (deidentified DB) available at https://www.kaggle.com/datasets/drscarlat/mimic3c/data

 It is classification problem : predict mortality based on the input parameters like gender, age and diagnosis
 
# Data Dictionary
* hadm_id:Admission identifier.
* gender: Patient's gender.
* age:Patient's age.
* LOSdays: Length of stay in days.
* admit_type: Type of admission (e.g., emergency, elective).
* admit_location:Location where the patient was admitted (Example: EMERGENCY ROOM ADMIT, CLINIC REFERRAL, ...)
* AdmitDiagnosis: Primary diagnosis for the admission (Example: PNEUMONIA, CONGESTIVE HEART FAILURE, ...)
* insurance: Type of insurance coverage. Example: Medicare, Medicaid, Private, ...
* religion: Definition: Patient's religious affiliation.
* marital_status:
* ethnicity: Patient's ethnicity or race (Example: WHITE, BLACK/AFRICAN AMERICAN, HISPANIC, ...)
* NumCallouts: Number of callouts or requests for the patient.Example: 0, 1, 2, ...
* NumDiagnosis: Number of diagnoses associated with the patient.
* NumProcs:Number of procedures performed on the patient.
* AdmitProcedure: Procedure(s) performed during admission (Example: TRACHEOSTOMY, ANGIOGRAM, ...)
* NumCPTevents: Number of Current Procedural Terminology (CPT) events. Example: 5, 0, 3, ...
* NumInput:Number of input events (e.g., medications, fluids).
* NumLabs:Number of laboratory tests conducted.
* NumMicroLabs: Number of microbiology lab tests.
* NumNotes:Number of clinical notes.
* NumOutput:Number of output events (e.g., urine output).
* NumRx: Number of prescription medications.
* NumProcEvents: Number of procedural events.
* NumTransfers: Number of patient transfers.
* NumChartEvents: Number of charted events.
* ExpiredHospital:Indicates whether the patient expired during the hospital stay (binary: 0 or 1)Example: 0 (Survived), 1 (Expired).
* TotalNumInteract: Total number of interactions/events recorded for the patient.
* LOSgroupNum: Length of Stay (LOS) group number, categorizing patients based on their ICU stay duration

* # EDA
### Diagnosis:
Most of the case are newborn 
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/28f62023-8ad3-4f8b-a251-20746ede450b)

### Survived X died 
It is unbalanced data so I will use SMOTE to oversample my data.
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/03e925cf-4ec7-400c-aea0-fc96c6612e7e)
 

### Heatmap
Expired has a higher correlation with 'NumInput', 'NumLabs', 'NumRx', 'NumChartEvents','TotalNumInteract'(> 0.3)

![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/cbfed6d1-2c63-42fc-9203-c0e64e7e8295)


### Age: 
The majority of surviving patients are newborns, with a median age of 58 years, which is 10 years younger than patients who did not survive, as their median age is 68 years.
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/f91de23d-3f0d-426b-8ef4-8ef71737b662)

![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/b9235299-37dd-493b-837e-68722d04d580)



### LoDays

There is no big difference between died and survived.
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/a2796035-233c-4a38-9714-9c5baf30ff5c)
  

### Admit type
More than 80% of patients who did not survive were emergency and 60% of patients who survived  

![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/84c20f2f-85fc-43e7-8076-dbcb7897772a)

### Top 20 AdmitDiagnosis distribution
Most of the patients who died were sepsis, pneumonia and intracranial hemorrhage 
Most of the patients who survived were newborn 
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/b3a8d3ce-db59-47a4-89d8-a034406fe0e2)

# ML 
![image](https://github.com/MileneCV/MIMIC3_TEST/assets/112773242/b3b03745-29df-4476-81f0-9c41091b5610)

To predict mortality the better model is one with a lower False negative rate and better recall. 
The best model was logistic regression, in the test data the accuracy was 87%, recall 77% and the false negative rate was 23%.




