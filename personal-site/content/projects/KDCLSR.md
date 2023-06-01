+++
title = "Selective Teacher Reliance for Knowledge Distillation"
description = "Knowledge distillation (KD) is a powerful, well established model compression technique that can face performance limitations when student models attempt to mimic large teacher models on high dimensional tasks like image classification (Cho and Hariharan, 2019). Motivated from ideas in curriculum learning, we explore the idea of selective reliance on the task of image recognition, where a student model relies more heavily on teacher guidance for data samples deemed difficult by a teacher generated curriculum. Experimental results show minimal effect of curriculum setting and selective reliance techniques on student accuracy and convergence. "
date = "2022-04-21"
aliases = ["about-us","about-hugo","contact"]
author = "Hasan Khan, Sarvani Nadiminty, Divya Amin"
+++

## Abstract

Knowledge distillation (KD) is a powerful, well established model compression technique that can face performance limitations when student models attempt to mimic large teacher models on high dimensional tasks like image classification (Cho and Hariharan, 2019). Motivated from ideas in curriculum learning, we explore the idea of selective reliance on the task of image recognition, where a student model relies more heavily on teacher guidance for data samples deemed difficult by a teacher generated curriculum. Experimental results show minimal effect of curriculum setting and selective reliance techniques on student accuracy and convergence. See the full report [here](/files/KD_Partial_Reliance.pdf).

## Introduction

Knowledge Distillation (Hinton et al, 2015) is a model compression technique commonly used in applied settings where large models are difficult to store and run. KD comprises of a dual model student-teacher framework, where a small capacity student model aims to mimic the performance of a larger capacity teacher model by learning the distribution of the output labels generated from the teacher model trained on the same dataset. More specifically, the student model uses a bipartite loss function L_student that incorporates both L_kd (the KD loss measured by the KL divergence between the softmax of the student output logits P_S and the softmax of the teacher output logits P_T, scaled by the temperature parameter τ) and L_ce (the standard cross entropy training loss using the true labels y_true). The parameter λ controls the weight given to each component loss. The student loss and its component losses are defined below:

$$ L_{ce} = CE(y_{true},P_S) $$
$$ L_{kd} = \tau^2 KL(P_T,P_S) $$
$$ L_{student} = (1 - \lambda)L_{ce} + \lambda L_{kd} $$


However, KD has been shown to provide minimal to no performance gains for certain tasks such as image recognition on ImageNet  (Zagoruyko and Komodakis, 2016). Cho and Hariharan (2019) examine the reasons behind failures in this context, noting that large differences in student teacher model capacities may limit the student model's ability to minimize both training loss and KD loss, forcing the student to minimize the KD loss over the train loss.

From this finding, we propose *selective reliance*, a technique for dynamically changing the student's reliance on KD loss by updating λ in L_{Student at the sample level, where λ is determined by the difficulty of the sample. Difficulty is defined in the context of Curriculum Learning (CL), a training strategy for improving model convergence speed and accuracy that involves training on easily learnable samples before difficult ones. 

Difficulty rankings for samples can be determined using the confidence scores of additional models, as outlined by Weinshall and Cohen (2018). In the context of knowledge distillation, we use the teacher model to be distilled as the scoring function (Haconen and Weinshall, 2018) for each datapoint in the the student's curriculum. We build closely on work conducted by Zhao et al (2021) where curriculum learning is also used to improve knowledge distillation on image recognition tasks, but aim to employ a distinct curriculum generation scheme from theirs, and a novel mechanism for its effect on KD loss utilization. We hypothesize that relying on the teacher is only in the student's best interest when the sample being evaluated is difficult, and that accuracy yielded from KD w/ CL (KD-CL) can be improved upon with selective reliance (KD-CL-SR) techniques built into KD. 

See the full report [here](/files/KD_Partial_Reliance.pdf).

