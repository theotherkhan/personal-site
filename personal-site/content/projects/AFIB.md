+++
title = "Detecting Atrial Fibrillation Burden Using 1-D CNNs"
description = "1-D CNNs have recently been used to classify various classes of Arrhythmias using ECG sequences. In this paper, a 1-D CNN is used to predict the Atrial Fibrillation (AF) burden of ECG sequences, which is a useful continuous metric that helps gauge AF severity and can be predictive for risk of near term stroke."
date = "2021-12-10"
aliases = ["about-us","about-hugo","contact"]
author = "Hasan Khan"
+++

## Abstract

1-D CNNs have recently been used to classify various classes of Arrhythmias using ECG sequences. In this paper, a 1-D CNN is used to predict the Atrial Fibrillation (AF) burden of ECG sequences, which is a useful continuous metric that helps gauge AF severity and can be predictive for risk of near term stroke. See the full paper [here](/files/HCML_Final_Project.pdf).

## Introduction

Anywhere from 2.7-6.0 million Americans suffer from Atrial Fibrillation, the leading type of heart arrhythmia (Mina, 2020). Atrial Fibrillation is characterized by an irregular heartbeat; if left untreated, it can lead to blood clots, stroke and other serious heart complications. Historically, cardiologists and technicians manually scan Electrocardiogram (ECG) recordings of patients to determine the presence of AF in patients, often with the assistance of peak detection and interval analysis algorithms. However, these algorithms have a high error rate (Shah, 2007), and in recent years, a plethora of statistical models and machine learning techniques such as Convolutional Neural Networks (CNNs) (Rajpurkar, 2017) and Markov Models (Coast, 1990), among others, have been successfully applied to arrhythmia and AF detection problems, often out preforming traditional methods. These models are attractive because they can help save cardiologist time, increase accessibility to AF diagnosis, and are especially effective for continuous monitoring when paired with wearable technologies that can measure ECG signals.

However, these techniques are often focused on the classification and sub typing of ECG sequences. In this project, the objective is modified to calculate the AF Burden of each sequence instead, a continuous variable defined as the proportion of an ECG sequence that displays AF characteristics. AF Burden has been shown to be associated with near term stroke risk (Lin, 2018), and depending on the duration of the ECG, can be used to help classify between variants of AF, such Paroxysmal AF (episodic AF) and Persistent AF (chronic AF). 

This project builds on previous AF classification techniques, modifying them slightly for the purposes of predicting AF Burden. ECG signals from the The 4th China Physiological Signal Challenge (Wang, 2021) are used as the input data for the model, from which the project is inspired. 

See the full paper [here](/files/HCML_Final_Project.pdf).