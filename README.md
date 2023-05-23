# Assymetric_CycleGAN_Inverse_Design_Metasurfaces
This is the relevant code for the Assymetric CycleGAN. 


## Introduction

The assymetric cycleGAN described in this github repository is a two directional transformation between a photoluminescent spectrum (PL Spectrum) and a target shape in the image space. This allows the Inverse Design (Spectrum to Shape) and Forward design (Shape to Spectrum) of metasurface sub-wavelength structures.

## Data format

The source data is of the form of roughly 18,000 images, and their respective reflectance spectrums. These are referred to as ground truth data, and the original dataset was sourced from the Raman Lab experiment using the cDCGAN which is available at the following link: https://github.com/Raman-Lab-UCLA/Multiclass_Metasurface_InverseDesign/tree/main

In this case, we implement the solution mainly using the tensorflow framework. Due to the different dimensionality present between the image data and the PL spectrum data, the data is converted to a tfrecord object within python, this is done within the first few blocks of code. Further information about tensorflow records can be found here: https://www.tensorflow.org/tutorials/load_data/tfrecord#:~:text=The%20TFRecord%20format%20is%20a,to%20understand%20a%20message%20type.

## Training Process

The CycleGAN is constructed through both one and two dimensional convolutional blocks, and the output can be displayed along the original data. The training process may not converge, and is extremely unstable. Depending on your dataset you may need to spend a significant time tuning hyperparameters to ensure the model does not converge too fast or too slow. 

The following module versions are needed:

- **Tensorflow 2.9.x**
- **Numpy version 1.x**

## Results

The following shows the noise improvement as a function of FID Score:

<img width="873" alt="Screen Shot 2023-05-23 at 2 01 10 pm" src="https://github.com/Jeygopi/Assymetric_CycleGAN_Inverse_Design_Metasurfaces/assets/69072732/1c13265d-4eb7-4b08-a656-78576931fb87">

The following are some example generated spectrums compared to their input result. The Forward Calculation was done through FDTD software to obtain an accurate numerical result:

<img width="877" alt="Screen Shot 2023-05-23 at 2 12 14 pm" src="https://github.com/Jeygopi/Assymetric_CycleGAN_Inverse_Design_Metasurfaces/assets/69072732/df600090-c7bc-4766-90e1-0d17addc886b">

## Notes

### Generalization

- The above code can be used for any two way transformation between datasets where one side is an image and the other side is some sort of time series data. 

- It is possible to convert the images to grayscale beforehand for faster processing, we noticed for this particular application this provided no improvement in terms of the final result.

- Changing input dimensions is something that would require significant work. We are currently working on an improved system regarding this. 
