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
