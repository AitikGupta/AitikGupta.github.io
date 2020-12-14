---
title: ActiveNet
layout: post
date: 2020-10-26 15:30
tag:
- PyTorch
- Machine Learning
- Computer Vision
- Human Pose Estimation
image: https://raw.githubusercontent.com/aaditagarwal/ActiveNet/master/screenshots/Below_25_2.png
headerImage: true
projects: true
hidden: true
description: A multi-stage mechanism to detect levels of activeness, with a single
  monocular image input of a person
category: project
author: aitikgupta
externalLink: false
---

#### ActiveNet is a multi-stage mechanism to detect levels of activeness, with a single monocular image input of a target person.
## In-Depth Details
Our paper, __ActiveNet: A computer-vision based approach to determine lethargy__ consists of in-depth details, literature review, experimentation results, etc. It can be found on [arXiv]({{ site.url }}/blog).
## Implementation Details
### Overview
<img width="75%" src="{{ site.url }}/assets/images/projects/ActiveNet_Objective.png">
#### Multi-stage flowchart of ActiveNet
<img width="175%" src="{{ site.url }}/assets/images/projects/ActiveNet_Flowchart.png">
#### Alert mechanism flowchart
<img width="75%" src="https://raw.githubusercontent.com/aaditagarwal/ActiveNet/master/screenshots/Alert_System_FlowChart.png">
## Modules
#### Human Pose Estimation
Modified [this implementation](https://github.com/Daniil-Osokin/lightweight-human-pose-estimation.pytorch) to interpolate 2 extra keypoints from ground-truth 17 keypoints, used their weights trained on [MSCOCO dataset](https://cocodataset.org/#keypoints-2020).
#### Pose Encoding
[This module](https://github.com/aaditagarwal/ActiveNet/blob/master/create_encoding.py) creates the angular encodings from bare keypoint annotations from HPE module.
#### Multi-Class Classification
Level of activeness assessed into 1 of 4 levels with a Decision-Tree based classifier, trained on a self-scraped dataset.
<p align="center" width="100%">
	<img width="24%" src="{{ site.url }}/assets/images/projects/ActiveNet_Level1.png" > 
	<img width="24%" src="{{ site.url }}/assets/images/projects/ActiveNet_Level2.png"> 
	<img width="24%" src="{{ site.url }}/assets/images/projects/ActiveNet_Level3.png"> 
	<img width="24%" src="{{ site.url }}/assets/images/projects/ActiveNet_Level4.png"> 
</p>
<figcaption>Levels of Activeness</figcaption>
### Alarm System
Low activeness alerts run out to users of a Slack Workspace.
## Conclusion
__Our paper has been accepted in [ACM India Joint International Conference on Data Science and Management of Data, (CoDS-COMAD '21)](https://cods-comad.in/2021/accepted_papers.html##blog-details:~:text=ActiveNet%3A%20A%20computer%2Dvision%20based%20approach%20to,Aitik%20Gupta%20and%20Aadit%20Agarwal)!__ \
The whole pipeline is open-sourced on [GitHub](https://github.com/aaditagarwal/ActiveNet).
