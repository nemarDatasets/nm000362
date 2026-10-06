The information available for download can be found in the following files:

WakefulnessAllRegions.zip: Compressed file containing all the signals organized in one edf file per brain region.

Information.zip: Contains thre csv files with Information about patients, brain regions, and channels.

MatlabFile.zip: Matlab file with all the signals and extra information in a single file.


Description of signals: 

Signals correspond to a quiet wakefulness state with eyes closed, non-REM sleep (stages N2 and N3), and REM sleep. A total duration of one minute recorded from up tp 1772 channels from 106 patients with focal epilepsy. Only channels located in the gray matter and deemed 'normal' were included (see Frauscher et al., 2018. Brain, 141:1130-44 for more information on the wakefulness data). For the N2 and N3 sleep stages only 1468 channels are available, and for REM sleep only 1012 (see von Ellenrieder et al., 2019, in preparation, for more information on the sleep data).

Preprocessing:
1. All signals were resampled to 200 samples per second (unless that was the original sampling rate), after applying a low-pass antialiasing filter at 80 Hz.
2. Power-line interference was reduced with an adaptive filter. This consisted on a high-pass filter at 48 Hz (FIR filter, order 100, 38-48 Hz transition band), followed by an instantaneous phase and amplitude estimation at the harmonics of the power-line frequency, smoothing of the estimate with a first order low-pass IIR filter, and subtraction of the estimated interference. First the third harmonic was estimated and subtracted, followed by the second harmonic, and the fundamental power-line frequency. The power-line frequency is 50 Hz for channels with name beginning with 'G', and 60 Hz for channels beginning with 'M' or 'N'.
3 Artifacts were visually detected by an experienced neurophysiologist, and excluded from the recording. This resulted in some patients having several non-consecutive segments to complete one minute of data. All the channels from each patient were recorded simultaneously.
4. The mean value of each segment and channel was subtracted from the corresponding segment and channel.
5. The segments were concatenated leaving a buffer time of 2 seconds of zero amplitude between segments. Since in at least one patient there were 5 segments, the total duration of the concatenated signal is 68 seconds. All the channels were then zero padded at the end to a length of 68 seconds (13600 samples) if necessary to have a uniform length regardless of the number of segments. 


Description of variables:

Channel Information:

Channel Type: Character indicating the type of electrodes used to record the signal 'D' for Dixi intracerebral electrodes, 'M' for homemade MNI intracerebral electrodes, 'A' fro AdTech intracerebral electrodes, 'G' for AdTech subdural strips and grids.

Patient: Id number of the patient. The numbers range from 1 to 110, but there are only 106 different patients (no suitable channels were found in patients 51, 86, 95, and 105, so these patients do not appear in the database).

Hemisphere: 'L' for channels recording from the left hemisphere, 'R' for channels recording from the right hemisphere.

Channel Name: The name of the channel is composed by two characters (the second one is the Channel Type), followed by three digits (the Id number of the patient), followed by 'L' or 'R' as in the Hemisphere variable, and then one or more characters and or numbers which correspond to the name of the electrode and contact number in the recording center, but convey no information. The last character indicates the sleep stage (W: wakefulness, N: stage N2, D: stage N3, R: REM sleep).

Channel Position: x,y, and z coordinates of the position of each channel in MNI space. To obtain it a nonlinear coregistration (two-step procedure, first an affine transformation followed by a nonlinear deformation) was computed between each subject's space (in which the contacts were identified) and the ICBM 2009a symmetric template (1x1x1 mm), the transformation was then applied to the electrode positions in native space. The channel position is the midpoint between the electrode contacts that make up each bipolar channel.

Channel Region: The brain region (1-38) to which the channel belongs. To obtain it a nonlinear coregistration (two-step procedure, first an affine transformation followed by a nonlinear deformation) was computed between the template (and associated segmentation) from Landman and Warfield (editors MICCAI 2012 Workshop on Multi-Atlas Labeling. Create Space Independent Publishing Platform; 2012)  and  each subject's space (in which the contacts were identified).


Brain region Information:

Region Name: Name of the brain regions of the segmented template, 1-38 gray matter regions and 39=white matter.


Patient Information:

Gender: 'M' or 'F' for the 106 patients.

Age At Time Of Study: in years, for the 106 patients.


Signals (in matlab file only):

Data_W: matrix with one column per channel, and 13600 samples containing all the signals for wakefulness.

Data_N2: Idem for sleep stage N2 signals. Missing channels are filled with NaNs.

Data_N3: Idem for sleep stage N3 signals.

Data_R: Idem for REM sleep signals.


SamplingRate: Sampling rate of the signals in samples per second, i.e. 200.


Geometric information (in matlab file only):

FacesLeft: faces of the tesselated cortical surface of the template used for the automatic segmentation, coregistered to MNI space, and extracted with FreeSurfer. The given surface corresponds to the middle of the gray matter, i.e. mid surface between pial and white surfaces, for the left hemisphere.

NodesLeft: nodes of the surface described above.

NodesLeftInflated: nodes of the inflated cortical surface described above, the same FacesLeft variable mentioned above should be used to display the surface.

NodesRegionLeft: One value for each node, it indicates the region number (1-39) for each point on the surface.

And the same variables for the right hemisphere.
