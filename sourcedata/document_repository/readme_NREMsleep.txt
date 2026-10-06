The dataset is in a matlab file containing the physiological sEEG recordings used to analyze spindles and sleep slow waves in:
-von Ellenrieder N, et al. How the human brain sleeps: Direct cortical recordings of normal brain activity. Annals of Neurology, epub Nov. 2019.  https://doi.org/10.1002/ana.25651
Please cite this paper if you use the data in your work.

Description of signals: 
Signals correspond to non-REM sleep (stages N2 and N3). A total duration of up to 10 minutes per stage recorded from 1468 channels from patients with focal epilepsy. Only channels located in the gray matter and deemed 'normal' were included.
Preprocessing:
1. All signals were resampled to 200 samples per second (unless that was the original sampling rate), after applying a low-pass antialiasing filter at 80 Hz.
2. Artifacts were visually detected by an experienced neurophysiologist, and excluded from the recording. This resulted in some patients having several non-consecutive segments to complete one minute of data. All the channels from each patient were recorded simultaneously.
3. The mean value of each segment and channel was subtracted from the corresponding segment and channel.
4. The segments were concatenated leaving a buffer time of 2 seconds of zero amplitude between segments. Since in at least one patient there were 9 segments in stage N2 and 13 in stage N3, the total duration of the concatenated signal is 10 min 18 seconds for stage N2 and 10 min 26 seconds for stage N3. All the channels were then zero padded at the end to that length if necessary to have a uniform length regardless of the number of segments. 


Description of variables:

Signals:
-Data_N2: sEEG recordings, one bipolar channel per column (in micro V).
-Data_N3: sEEG recordings, one bipolar channel per column (in micro V).
-SamplingFrequency: Sampling rate of the signals in samples per second, i.e. 200.
Channel Information:
-ChannelType: Character indicating the type of electrodes used to record the signal 'D' for Dixi intracerebral electrodes, 'M' for homemade MNI intracerebral electrodes, 'A' fro AdTech intracerebral electrodes, 'G' for AdTech subdural strips and grids.
-Patient: Id number of the patient. The numbers range from 1 to 110, but there are less patients with actual data.
-Hemisphere: 'L' for channels recording from the left hemisphere, 'R' for channels recording from the right hemisphere.
-ChannelName: The name of the channel is composed by two characters (the second one is the Channel Type), followed by three digits (the Id number of the patient), followed by 'L' or 'R' as in the Hemisphere variable, and then one or more characters and or numbers which correspond to the name of the electrode and contact number in the recording center, but convey no information. The last character indicates the sleep stage (W: wakefulness, N: stage N2, D: stage N3, R: REM sleep).
-ChannelPosition: x,y, and z coordinates of the position of each channel in MNI space in mm. To obtain it a nonlinear coregistration (two-step procedure, first an affine transformation followed by a nonlinear deformation) was computed between each subject's space (in which the contacts were identified) and the ICBM 2009a symmetric template (1x1x1 mm), the transformation was then applied to the electrode positions in native space. The channel position is the midpoint between the electrode contacts that make up each bipolar channel.
-ChannelRegion: The brain region (1-38) to which the channel belongs. To obtain it a nonlinear coregistration (two-step procedure, first an affine transformation followed by a nonlinear deformation) was computed between the template (and associated segmentation) from Landman and Warfield (editors MICCAI 2012 Workshop on Multi-Atlas Labeling. Create Space Independent Publishing Platform; 2012)  and  each subject's space (in which the contacts were identified).
Brain region Information:
-RegionName: Name of the brain regions of the segmented template, 1-38 gray matter regions and 39=white matter.
