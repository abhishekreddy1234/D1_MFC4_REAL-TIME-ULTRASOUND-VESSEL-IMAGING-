# D1_MFC4_REAL-TIME-ULTRASOUND-VESSEL-IMAGING-
This repository describes a high-speed method for ultrasound micro-vessel imaging. It uses randomized singular value decomposition (rSVD) and spatial downsampling to filter out tissue clutter in real-time. Tested on a Verasonics system, it achieves a frame rate of 22 Hz, significantly reducing computational time without losing image quality.
Team Members Name and Roll Number
   K. ABHISHEK – CB.SC.U4AIE24325P.     MOKSHAGNA ARYAN –CB.SC.U4AIE24341
   RISHIKESH – CB.SC.U4AIE24365
Base/Reference PaperTitle: "Real time SVD-based clutter filtering using randomized singular value decomposition and spatial downsampling for micro-vessel imaging on a Verasonics ultrasound system".
Authors: U-Wai Lok, Pengfei Song, et al..
Publication: Ultrasonics, Volume 107, 2020.3.
Project Outline:-
The project implements a high-speed ultrasound imaging method designed to detect slow blood flow in micro-vessels by removing strong tissue clutter.
Core Algorithms: It combines Randomized Singular Value Decomposition (rSVD) to estimate the tissue clutter subspace with Randomized Spatial Downsampling (rSD) to break large data matrices into smaller sub-matrices.
Parallel Execution: These sub-matrices are processed independently across multiple CPU cores using a multi-threaded architecture (pthreads).
Noise Management: The system incorporates a noise subtraction technique that estimates background electronic noise power and removes it from the final power Doppler image.4.
Updates Implementation & Achievement:
The system was successfully deployed on a Verasonics Vantage scanner using a 12-core CPU architecture.
Speed & Efficiency:The processing time for the rSVD clutter filter is less than 30 ms.
A real-time frame rate of 22 Hz was achieved for micro-vessel imaging.
Imaging Quality: The Blood-to-Clutter Ratio (BCR) consistently exceeded 20 dB when using optimized settings (block size of $30 \times 30$, ensemble size of 45, and a tissue rank of 26).
Performance Comparison: Testing showed that the rSVD+rSD method provides similar clutter rejection performance to "global" SVD but with significantly lower computational complexity.
Challenges / Issues FacedComputational Bottleneck: Standard SVD is too slow for real-time applications, taking over 5 seconds for a single frame on some hardware.
Separation Difficulty: High-pass filters often fail to separate slow blood flow from moving tissue clutter.
Electronic Noise: Ultrafast imaging is highly sensitive to electronic noise, which creates a "ramp-shaped" background that obscures small vessels.
Threshold Selection: A major challenge in SVD filtering is determining the exact rank (threshold) needed to separate tissue from blood without losing vital signal.
Future Plans 
(Understanding rSVD and rSD)Understanding rSVD Mechanics: Deepening knowledge of how rSVD uses random matrix projection and QR decomposition to approximate the first k singular values (tissue clutter) at a fraction of the cost of full SVD.
Mastering rSD Parallelism: Learning how randomized spatial downsampling eliminates "gridding artifacts" typically caused by uniform downsampling while enabling efficient multi-core processing.
