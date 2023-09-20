# VAE-Latent-Space-Exploration
This repo is my attempt to recreate the preprocessing steps and training of a VAE as outlined in the IEEE research paper "Examining the Size of the Latent Space of Convolutional Variational Autoencoders Trained with Spectral Topographic Maps of EEG Frequency Bands"

This project is a work in progress. 

This is primarily done using Google Colab. Preprocessing is performed in "EEG_preprocessing.ipynb", training is done in "VAE_training.ipynb"

## Preprocessing 
The preprocessing pipeline can be divided into 3 main sections with substeps for each section. The preprocessing was done as described in the paper "Examining the Size of the Latent Space of Convolutional Variational Autoencoder Trained with Spectral Topographic Maps of EEG Frequency Bands". <br>

Code below is divided as follows:

1. Loading Data <br>
  Unzips data from .dat file

2. EEG signal preprocessing <br>
   For each participant, the following preprocessing steps are done to the EEG signals: <br>
  
  - EEG data is split into discrete time-slices
  - FFT and PSD is applied to each time slice. Power spectrum is divided into 5 EEG bands (delta, theta, alpha, beta, gamma)
  - Centroid frequency amplitude is calculated for each EEG band and then normalized.

3. Creating topgraphic head map <br>
  - Topo data for each waveband is created by plotting the centroid data onto a 2D head map.
  - Data from head map is converted into a numpy array.
  - Each topographic headmap for each waveband is combined to create a 5 channel tensor of size 32x32x5
  - Data is then saved. File path to save the resulting data will need to be specified
  - A folder is created for each time slice applied (0.5, 1.0, 1.5 & 2 seconds). 

## Training the VAE - Work in progress
After applying the preprocessing pipeline. I will be feeding the data into a VAE model to try and replicate the results obtained in the referenced paper. The VAE model used [2] was adapted from the github repo "VAE_Reconstruction_Classification"

## References 
[1] “Examining the Size of the Latent Space of Convolutional Variational Autoencoders Trained With Spectral Topographic Maps of EEG Frequency Bands”, TAUFIQUE AHMED, LUCA LONGO

[2] "VAE_Reconstruction_Classification" (https://github.com/inDSweTrust/VAE_Reconstruction_Classification)


