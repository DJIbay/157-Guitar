# 157-Guitar
Visualizing Sound: String Motion Tracking and Frequency Analysis

Motivation

Sound is a physical phenomenon rooted in wave motion. Musical instruments like guitars convert mechanical vibrations in the form of moving strings into sound waves, which can be understood more deeply by analyzing the underlying motion dynamics. The motivation for this project is to visualize and quantify the motion of a vibrating guitar string, using frame-by-frame image processing and Fourier analysis to demonstrate how visual data can be bridged to acoustic behavior. By approximating the shape of the string over time, the objective is to track its motion and to then identify the dominant frequency it produces and compare it to the theoretical expectations for the known string.

Approach

A 60 fps video slowed to 40% speed of a guitar being strummed was preprocessed to crop the region of interest (E2 string) and enhance the visibility of the string. Morphological operations were used to clean up and isolate the string from the background, and its curved shape was extracted from each frame using various filtering methods.

A vertical probe line was selected at a fixed y-position to track the lateral displacement of the string across time. This produced a one-dimensional time series representing the string’s motion at that cross-section. The signal was detrended and windowed before applying a real-valued fast Fourier transform (rFFT) to analyze its frequency content.

Due to the frame rate being lower than twice the theoretical frequency, aliasing was present in the observed spectrum. An alias-correction algorithm was implemented to estimate the theoretical frequency based on the observed aliased peak, the known frame rate, and a select n value.

Analysis

The extracted displacement signal revealed a strong periodic behavior corresponding to the string's oscillation. Fourier analysis of the windowed signal showed a dominant aliased frequency of 8 Hz. Based on an expected theoretical frequency of 82.4 Hz for the E2 string and a frame rate of 24 fps, the aliasing correction identified the estimate frequency as 80 Hz, significantly close to the theoretical value.

The presence of higher harmonics was also detectable in the frequency spectrum, though their relative amplitudes varied depending on damping effects. This aligns with the harmonic nature of vibrating strings, where integer multiples of the fundamental frequency contribute to the overall motion and tone.

Key Takeaways

  A vibrating guitar string's motion can be effectively captured and analyzed using frame-by-frame image processing.
  Visually, the string does behave as transverse standing waves, with distinct nodal patterns and curved motion that can be digitized as analog    motion.
  Tracking lateral displacement over time allows reconstruction of the string’s vibration as a 1D time-evolving signal.
  Fourier analysis reveals the frequency content, confirming both the fundamental and harmonic components of the string’s sound.
  This method opens opportunities for visual and quantitative studies of musical acoustics and wave mechanics using accessible tools.
