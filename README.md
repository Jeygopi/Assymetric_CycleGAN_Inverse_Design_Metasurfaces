# Assymetric_CycleGAN_Inverse_Design_Metasurfaces
This is the relevant code for the Assymetric CycleGAN. 


## Introduction

The assymetric cycleGAN described in this github repository is a two directional transformation between a photoluminescent spectrum (PL Spectrum) and a target shape in the image space. This allows the Inverse Design (Spectrum to Shape) and Forward design (Shape to Spectrum) of metasurface sub-wavelength structures.

## Data format

The source data is of the form of roughly 18,000 images, and their respective reflectance spectrums. These are referred to as ground truth data, and the original dataset was sourced from the Raman Lab experiment using the cDCGAN which is available at the following link: https://github.com/Raman-Lab-UCLA/Multiclass_Metasurface_InverseDesign/tree/main

In this case, we implement the solution mainly using the tensorflow framework. Due to the different dimensionality present between the image data and the PL spectrum data, the data is converted to a tfrecord object within python, this is done within the first few blocks of code.

## Training Process

The CycleGAN is constructed through both one and two dimensional convolutional blocks, and the output can be displayed along the original data. 
