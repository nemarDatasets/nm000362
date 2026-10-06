These files contain the raw data of physiological sEEG recordings used to analyze HFOs in:

-Frauscher B, et al. High frequency oscillations in the normal human brain. Annals of Neurology, 2018.

Please cite this paper if you use the data in your work.

In adition to this file there are four Matlab data (.mat) files, a matlab function (.m) file, and two NifTi (.nii) files.
The Matlab files contain the sEEG Data, separated in four groups according to the sampling rate and the type of sEEG electrodes used for recording (DIXI electrodes or MNI Home Made (HM) electrodes).

Each .mat file contains the following variables:
-Data: sEEG recordings, one bipolar channel per column. This is an int16 variable to reduce storage requirements. In order to obtain the recordings in uV this matrix should be multiplied by the Gain variable.
-Gain: The constant needed to convert the Data to micro-Volts.
-Patient: A vector identifying the patient to which each channel corresponds (i.e. channels with equal patient number are from the same patient).
-Channel: A cell array with the original name of each channel.
-Position: Talairach coordinates of the channels (midpoint of bipolar channels), in mm.
-Region: A number identifying the brain region to which each channel belongs, there are 17 different regions.
-RegionList: Cell array with the name of the 17 regions.

The function file corresponds to the HFO Detector code.

The NifTi files correspond to a brain template and a brain segmentation into the 17 used regions. These files are modified versions of an existing ATLAS (Landman BA, Warfield SK, editors. MICCAI 2012 Workshop on Multi-Atlas Labeling. Create Space Independent Publishing Platform; 2012). They were non-linearly registered to the ICBM152 2009c nonlinear symmetric brain model (Mazziotta J, Toga A, Evans A, Fox P, Lancaster J, Zilles K, et al. A probabilistic atlas and reference system for the human brain: International Consortium for Brain Mapping (ICBM). Philosophical transactions of the Royal Society of London Series B, Biological sciences 2001:356:1293-1322; Fonov V, Evans AC, Botteron K, Almli CR, McKinstry RC, Collins DL, et al. Unbiased average age-appropriate atlases for pediatric studies. Neuroimage 2011;54:313-327), and the regions of the original segmentation were joined to form the 17 used regions.
