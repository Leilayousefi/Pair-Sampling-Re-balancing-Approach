# Pair-Sampling-Re-balancing-Approach

1.	Discretise DIABETES DATA
2.	Choose a specific Complication (such as retinopathy, liver or hypertension).
3.	Correction of comorbidities: Once the specific complication has diagnosed (one appeared at a visit of a patient then the following visits should remain as it was diagnosed and all ones except Negative cases (patients with all zero visits). 
4.	Choose the patients which are not diagnosed as having the complication in the first visit and ignore the rest of patients.
5.	Define an index variable that represent the first one (diagnosed happened) in the patient visits. 
6.	For all patients count the Positive and Negative cases.
7.	Find indices of patients having the complication (positive cases) and indices of patients not having the complication (negative cases).
8.	Create Positive Cell arrays of patients by randomly chosen from positive cases. 
9.	Create Negative Cell arrays of patients by randomly chosen from Negative. 
10.	If Positive cases is less than negative cases then data is unbalanced and needs to be balanced, then:
•	To the size of different of positive and Negative cases randomly resample positive cases and increase the size of Positive Cell to the Negative cell.
•	Shuffle and randomly select Positive Cell and Negative cell.
11.	Else if Positive cases is equal or greater than negative cases. then data is balanced and no needs to be balanced, then:
•	Resample positive cases as the size of negative cases (Times 3 to be big enough to be compared in confusion matrices of other complications).
•	Resample negative cases as the size of positive cases (Times 3 to be big enough to be compared in confusion matrices of other complications).
•	Shuffle and randomly select Positive Cell and Negative cell.

12.	Now We have Positive and Negative cases with the same size as each other and need to split out(half of each for test set and the second half for train set, each into two cases to be fitted into the test set and train set as having both the same amount of positive and negative cases.
13.	Randomly combine Positive and Negative cases into train cell and test cell.
14.	Check if there are elements of new positive CELL ARRAY that are not in Primary positive cases and if necessary add them.                     
15.	For all patients in the test set select a pair of only two visits:
•	If negative cases (not diagnosed) the randomly choose one visit of the patient and the following time series visit as creating pair visits in an array ([0 0]) 
•	or If positive cases (was diagnosed) choose the first visit of the patient that complication was diagnosed (diagnosis point) and the previous time series visit as creating pair visits in an array ([0 1])
•	find the prediction point with searching the prediction set and by choosing a specific Threshold (1=<Threshold>0)

16.	 Create CONFUSION MATRIX as below:   
                
•	if any(DiagnosisPoint >= PredictionPoint+1)
                           Then TRUE_POSITIVE
                           TRUE_POSITIVE = TRUE_POSITIVE + 1;
                           CONFMAT{var} = [CONFMAT{var};[1 1]];
•	elseif ~any(DiagnosisPoint) && ~any(PredictionPoint)
                            Then TRUE_NEGATIVE
                            CONFMAT{var} = [CONFMAT{var};[0 0]];
                   
•	elseif ~any(DiagnosisPoint) &&      any(PredictionPoint) 
                           Then FALSE POSITIVE 
                            CONFMAT{var} = [CONFMAT{var};[0 1]];
•	elseif any(DiagnosisPoint) && ~any(PredictionPoint)
                           Then FALSE NEGATIVE
                             CONFMAT{var} = [CONFMAT{var};[1 0]];
                     End.    
 




![image](https://user-images.githubusercontent.com/22730314/116396691-96a75a00-a81d-11eb-9df7-37a816e84dd7.png)
