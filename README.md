How to run the code:
* Keep all the .mat files included in the zip folder in the same directory as the .ipynb files.
* Run Extra_Credit file separately

Limitations:
* Accuracy of Ses-Retest data is not as good as accuracy of Ses-test data (81% vs 91% without PCA)
* Better re-alignment and masking techniques could be used to improve accuracy
* Parameter tuning for Ses-Retest could be done over a greater range of values. Grid Search could be employed to obtain better results

Approach and Results:
* Both ses-test and retest data were realigned using SPM and masks were calculated using the realigned images using Imcalc in SPM (600_job.m and 600trainmaskjob_m)
* Mask of dimension 64x64x30 was applied to each 64x64x30 image to extract 184 features which were stored in a 1-D array.
* The features were fed to a SVM whose parameters were tuned using 3 ‘for’ loops. One for loop iterated over possible values of the C parameter, one for loop iterated over Gamma and one for loop iterated over random_states.
* Results for PCA were obtained by varying the number of components and best accuracy was obtained using n_components between 90 and 110
* SVM without PCA performed better than SVM+PCA possibly because PCA got rid of certain components which were important for accurate classification.
* SVM+PCA gave either lower or equal accuracy to pure SVM even after tuning.
* The results show that which area of the brain was responsible for which part of the body getting activated(foot,finger,etc.) by classifying the data with a maximum of 91% accuracy using SVM.


