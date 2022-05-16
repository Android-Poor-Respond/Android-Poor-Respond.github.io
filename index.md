## Android Poor Responsiveness

### Introduction
Almost all Android users have ever experienced poor responsiveness,
including the common frame dropping events---slow rendering (SR) and frozen frames (FF),
as well as the uncommon Application Not Responding (ANR) and System Not Responding (SNR) that directly disrupt user experience.
This work takes two complementary approaches, *controlled benchmarking* and *in-the-wild crowdsourcing*,
to comprehensively understand their	prevalence, characteristics, and root causes,
which turn out to be significantly different from common understandings and prior studies.
We find that SR, FF, ANR, and SNR all occur prevalently on all the studied hardware models of Android phones,
and better hardware does not seem to relieve ANR/SNR.
Most surprisingly, they are oftentimes ascribed to defective software design that incurs substantial resource overuse---lightweight apps can experience severe SR/FF events due to *redundant UI rendering*,
and the most ANR/SNR events stem from Android's aggressive implementation of *write amplification mitigation*.
In fact, the former can be effectively overcome by simplifying the apps' UI hierarchy,
and we design a practical approach to address almost all (>99%) of the latter
while only decreasing 3% of the data write speed with large-scale deployment.
We have released our measurement code/data to the research community.

### Measurement Code and Data

Currently, we have partially released our measurement code and data as follows. 
We plan to release all code and data after we get approval from the authority.

#### Measurement Code

* SR/FF Benchmark Framework and Analysis Tool

  The SR/FF benchmark framework and analysis tool are in [GitHub](https://github.com/Android-Poor-Respond/FrameAnalysis). 

* ANR/SNR Monitor Infrastructure

  The monitor infrastructure in our Android-MOD is implemented in [Monitor.java](https://github.com/android-poor-respond/Measurement/blob/master/code/Monitor.java).

* Root Cause Analysis Pipeline

  Our root cause analysis pipeline is implemented in [Pipeline.java](https://github.com/android-poor-respond/Measurement/blob/master/code/Pipeline.java).

* Regular Expressions

  Our leveraged regular expressions are listed in [Regex.java](https://github.com/android-poor-respond/Measurement/blob/master/code/Regex.java).

#### Measurement Data

We provide some measurement data on [github](https://github.com/android-poor-respond/Measurement/tree/master/dataset).

The attributes of each ANR/SNR event in the data are organized as follows:

* report_id

  The ID of a reported event.

* android_version

  The Android version.

* type

  The type of the event. Specifically, exp_anr denotes an ANR event and exp_jwdt denotes an SNR event.

* pid

  The ID of the app/critical process.

* process_name

  The name of the app/critical process.

* log

  The file name of the log file.
