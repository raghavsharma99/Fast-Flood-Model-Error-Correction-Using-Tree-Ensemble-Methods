# cs229 Final Project
cs229 Fast Flood Correction Model - Sharma and Tanh

# Motivation

Climate Change has increased both the likelihood and intensity of extreme hydrologic events like coastal floods which is exacerbated by rising sea levels. HighTide Intelligence is a flood intelligence startup that has developed a holistic flood risk engine made possible by their fast flood model. This summer, Raghav interned at HighTide to do an accuracy and uncertainty analysis of their fast flood model with respect to a computationally-intensive but more accurate Computational Fluid Dynamics
(CFD) model. However, setting up and running the CFD model is tedious, necessitating a more time-efficient method for evaluating uncertainty without multiple runs of the CFD model for different water level forcings. A machine learning model can be used to predict uncertainty at every location of the domain using physical/hydrologic features and estimated uncertainties from past model runs, helping scale our uncertainty analysis for different water level forcings, topographies, and storm
approaches.

# Methodology

This repo contains the required dataset and jupyter notebooks for the fast flood model uncertainty prediction task.
Each point in the dataset represents a 3mx3m tile containing domain specific information on topographic and physical features. Our task is to predict the diffference between a CFD Model and a Fast Flood Model at each tile in the domain given the features:

• Inland distance from the coastline - meters (int)
• Distance from the nearest water body - centimeters (int)
• Elevation with respect to North American Vertical Datum (NAVD 88) - meters (float)
• Water Level Forcing used in the flood models (storm surge height with respect to NAVD88) - meters (int)
• Flood depth output of the fast flood model - meters (float)

Target Variable - Difference (m)

We have decided to pose this uncertainty prediction problem as a classification task where the differences have been binned into 100 classes.
The predicted class will be transformed back to the difference values and the model performance will be evaluated by comparing the continous target variable instead of the predicted classes.

We have decided to use Tree-ensemble methods for the classification task and aim to experiment with Random Forest Classifier and XGBoost CLassifier.


