# Shortcut Learning PoC: Skin Lesion Classifiers
**Dark Side of AI/ML — Medical Imaging Project Proof of Concept**

## Overview
This proof of concept demonstrates the phenomenon of shortcut learning in medical imaging classifiers. Specifically, it highlights how a skin lesion classifier can learn to attend to synthetic artifacts rather than the actual lesion features. 

## Methodology
The project follows a structured pipeline to inject and expose shortcut learning:
* **Dataset Configuration:** Loads a subset of the ISIC 2018 dataset, specifically building a balanced subset of 500 malignant and 500 benign images.
* **Artifact Injection:** Injects a synthetic artifact onto all malignant training images.
* **Model Training:** Fine-tunes an `EfficientNet-B0` model on the corrupted dataset.
* **Evaluation:** Shows accuracy drops when the artifact is removed at test time.
* **Interpretability:** Visualizes `GradCAM` heatmaps to confirm that the model attends to the patch instead of the lesion.

## Future Work
* **Natural artifacts:** Repeat the experiment with real confounders flagged in the ISIC metadata, such as rulers and ink markings.
* **Demographic stratification:** Measure accuracy drops separately for Fitzpatrick skin type I-II vs V-VI to see if the bias is inequitably distributed.
* **Artifact removal augmentation:** Show that inpainting or cropping the artifact at training time reduces the shortcut as a mitigation strategy.
* **Broader architectures:** Test ResNet-50 and ViT-B/16 to see if transformer architectures are more or less susceptible to these shortcuts.
