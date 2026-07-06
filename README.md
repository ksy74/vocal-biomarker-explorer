# Vocal Biomarker Explorer

**Live demo: [ksy74.github.io/vocal-biomarker-explorer](https://ksy74.github.io/vocal-biomarker-explorer/)**

An interactive research demo exploring how acoustic features of sustained vowel phonation relate to the likelihood of Parkinson's-associated vocal impairment. Adjust the sliders (or record your own sustained "ahh") to see how a logistic regression model scores the input, with a live probability gauge and per-feature contribution breakdown.

## Model & methodology

The model is an 8-feature logistic regression fit to the public [Oxford Parkinson's Disease Detection dataset](https://archive.ics.uci.edu/dataset/174/parkinsons) (195 sustained-vowel recordings from 32 individuals), using pitch, amplitude, and nonlinear frequency-instability measures (Fo/Fhi/Flo, PPE, spread1/spread2, APQ, NHR). It was evaluated with patient-independent cross-validation (no individual's voice appears in both training and test) and achieves an AUC of 0.79, with a 0.5 screening threshold (89% sensitivity / 35% specificity) and a 0.91 confirmatory threshold (50% sensitivity / 94% specificity).

Paper: *forthcoming — link will be added here once published.*

## Record your own voice

The "Record your voice" panel captures ~5 seconds of sustained vowel audio in-browser (Web Audio API, no server, no upload) and estimates several of the model's input features client-side: pitch range via YIN pitch detection is reasonably reliable, while the three nonlinear features (PPE, spread1, spread2) are flagged with an "approx." badge since they're rough entropy/variability proxies, not the original nonlinear dynamical measures from the source dataset.

## Disclaimer

This is a research and educational demonstration, **not a diagnostic tool**. The model has not been validated on an external cohort and should not be used to assess any real individual. Features estimated from a live recording are additionally limited by an uncalibrated consumer microphone and simplified browser-side signal processing — they are not produced by the clinical MDVP acoustic analysis software the underlying model was actually trained on.
