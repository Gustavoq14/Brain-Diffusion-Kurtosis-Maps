# Obtaining-Maps-of-the-Apparent-Diffusion-Coefficient-and-Apparent-Kurtosis-in-Human-Brain
The present functions were developed in MATLAB R2017b (The MathWorks, Inc) as part of my special undergraduate [Thesis work](https://www.researchgate.net/publication/332705479_Analisis_de_la_Difusion_y_Curtosis_Aparentes_en_Imagenes_de_Resonancia_Magnetica) to qualify for the Bachelor Degree in Physics. In this Thesis work were obtained the maps for the apparent diffusion coefficient and apparent kurtosis of the brain of a healthy person. Afterwards, a segmentation was carried out in the three types of tissue of interest for this specific study (gray matter, white matter and cerebrospinal fluid) in order to classify the values of apparent diffusion coefficient and apparent kurtosis obtained in the maps, within the three types of tissues studied.

# Function-IDP.m
For this function input N is the file '' .mat '' taken from [Dryad](https://datadryad.org/stash/dataset/doi:10.5061/dryad.9bc43), this function allows to obtain the weighted diffusion image associated with each of the 19 slices of the human brain under study.

# Function-Setting.m
For this function, the M input is the output of the IDP.m function, this function allows obtaining the maps of the diffusion coefficient and apparent kurtosis associated with each of the 19 slices of the human brain under study.

# Function-Classification.m
For this function the entries LCR, MB, MG are the maps of Cephaloraquid Fluid, White Matter and Gray Matter obtained from the segmentation made with the software SPM12 to the images associated to the value of b = 0 s / mm2 for each slice of the human brain in study, and the CDA and CA inputs correspond to the outputs of the Adjustment.m function

The output [x, y, x1, y1, x2, y2] corresponds to the diffusion and apparent kurtosis values   associated with each type of tissue.

# Function-Results.m
This function is executed after executing the Classification function, its result is the average value of the diffusion and apparent kurtosis in each type of tissue of each slice.
