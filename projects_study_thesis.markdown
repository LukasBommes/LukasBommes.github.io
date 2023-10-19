---
layout: page
title: Predictive Maintenance of CNC Machines (Study Thesis)
permalink: /projects/study_thesis/
---

*Conducted during*: Study thesis at IWF TU Braunschweig and A\*Star SIMTech Singapore / Student research assistant at IWF TU Braunschweig 

*Topic*: Application of machine learning algorithms for the detection of anomalous components in a CNC milling machine

**Motivation**: Early detection of wear and failures in complex CNC machines is important to prevent costly standstills of production lines and further damage to the machine and other equipment.

**Aim**: Develop a method for anomaly detection in CNC machine tools. For easy deployment and compatibility with many machine tool manufacturers, the method must not rely on communication with the internal machine controller. Instead, the method must be based solely on the measurement of the total current consumption of the machine.

**Method**: To detect anomalous machine components, a machine program is run that activates machine axes sequentially and in a controlled way. The program is run once on the healthy machine to generate reference data and then executed in regular intervals for automatic inspection of the machine. During execution of the program the total current consumption is measured at a rate of 50 Hz and automatically cut into segments of individual axis’ movements by means of template matching (see fig. 1). Signal processing techniques and machine learning classifiers determine, whether additional (not directly controllable) aggregates, such as coolant pumps, are activated. For the creation of datasets for the machine learning algorithms a MATLAB-based annotation tool was built (see fig. 2). Hand-crafted features are extracted from clean segments (segments with all additional aggregates deactivated) and clustered. Anomalies are detected by distance thresholding between corresponding clusters of the reference dataset of the healthy machine and the current measurement (see fig. 3). Moreover, random faults are detected by an outlier search based on the local outlier factor. Experiments showed that this approach is sensitive enough to detect minor changes on the milling machine, such as removal of the tool from the main spindle.

![automatic_cuts_evaluation_z_axis](/assets/projects/images/automatic_cuts_evaluation_z_axis-1.png)
*Fig. 1: Section of the measured total current consumption of the machine tool with automatically detected segments (red lines).*

![label_assistant_window](/assets/projects/images/label_assistant_window.PNG)
*Fig. 2: Graphical user interface for manual data annotation built with MATLAB.*

![scatterplot](/assets/projects/images/scatterplot_result_experiment_2-1.png)
*Fig. 3: Clustered segments of the healthy reference machine (training) and the same machine with anomalies (testing) in classes 6 and 7, corresponding to the forward/backward movement of the z-axis.*

**Note**: We tested this method on a CNC mill at IWF TU Braunschweig and a much larger CNC lathe at Siemens Energy in Duisburg.

## Downloads

- [Study thesis (PDF)](/assets/documents/study_thesis.pdf)
