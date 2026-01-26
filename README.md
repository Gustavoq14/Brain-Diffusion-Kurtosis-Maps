# Obtaining Maps of the Apparent Diffusion Coefficient (ADC) and Apparent Kurtosis (AK) in the Human Brain

This repository contains a suite of functions developed in **MATLAB R2017b** (The MathWorks, Inc.) for processing Diffusion Magnetic Resonance Imaging (dMRI) data.

These tools were created as part of my [Undergraduate Physics Thesis](https://www.researchgate.net/publication/332705479_Analisis_de_la_Difusion_y_Curtosis_Aparentes_en_Imagenes_de_Resonancia_Magnetica). The project focuses on generating parametric maps of the **Apparent Diffusion Coefficient (ADC)** and **Apparent Kurtosis (AK)** from a healthy human brain, followed by tissue segmentation into Gray Matter (GM), White Matter (WM), and Cerebrospinal Fluid (CSF).

---

## Data Processing Pipeline

The project is structured into four main stages. The functions must be executed in the following order:

| Step | Function | Description | Input Source |
| :--- | :--- | :--- | :--- |
| **1** | `IDP.m` | **Data Extraction:** Retrieves weighted diffusion images for the 19 brain slices. | `.mat` file from [Dryad](https://datadryad.org/stash/dataset/doi:10.5061/dryad.9bc43) |
| **2** | `Setting.m` | **Map Calculation:** Fits the diffusion model to obtain ADC and AK maps. | Output from `IDP.m` |
| **3** | `Classification.m` | **Tissue Segmentation:** Classifies values into CSF, WM, and GM. | SPM12 masks and `Setting.m` output |
| **4** | `Results.m` | **Statistical Analysis:** Calculates mean values per tissue type and slice. | Output from `Classification.m` |

---

## Function Details

### `IDP.m`
Processes the raw input `N` (the `.mat` file from Dryad). It extracts and organizes the diffusion-weighted signal intensity for each of the 19 anatomical slices under study.

### `Setting.m`
Performs the mathematical fitting of the diffusion signal. The input `M` is the output from `IDP.m`. This function generates the quantitative maps for both the **Diffusion Coefficient** and **Apparent Kurtosis**.

### `Classification.m`
Integrates the computed maps with anatomical segmentations. It requires:
* **Tissue Masks:** CSF, WM, and GM maps obtained via **SPM12** segmentation (using $b = 0 \text{ s/mm}^2$ images).
* **Quantitative Data:** The ADC and AK maps from the previous step.

The output `[x, y, x1, y1, x2, y2]` provides the specific diffusion and kurtosis distributions for each tissue class.

### `Results.m`
The final stage of the pipeline. It aggregates the classified data to provide the average ADC and AK values for each tissue type across all 19 slices, facilitating comparative analysis.

---

## Academic Context
This work was developed to qualify for a **Bachelor’s Degree in Physics**. The methodology demonstrates the application of physical modeling to clinical neuroimaging data to characterize brain microstructure.

---
**Note:** For more detailed information on the mathematical models used, please refer to the full [Thesis work](https://www.researchgate.net/publication/332705479_Analisis_de_la_Difusion_y_Curtosis_Aparentes_en_Imagenes_de_Resonancia_Magnetica).
