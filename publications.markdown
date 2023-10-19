---
layout: page
title: Publications
permalink: /publications/
---

These are my peer-reviewed journal and conference publications

<h4 id="publication-1">[1] L. Bommes, T. Pickel, C. Buerhop-Lutz, J. Hauch, C. Brabec, and I. Peters, “Computer vision tool for detection, mapping, and fault classification of photovoltaics modules in aerial IR videos,” Progress in <em>Photovoltaics: Research and Applications</em>, vol. 29, no. 12, pp. 1236–1251, 2021. DOI: <a href="https://doi.org/10.1002/pip.3448">10.1002/pip.3448</a>.</h4>

<details style="margin-bottom: 10px;">
  <summary>Abstract</summary>
Increasing deployment of photovoltaics (PV) plants demands for cheap and fast inspection. A viable tool for this task is thermographic imaging by unmanned aerial vehicles (UAV). In this work, we develop a computer vision tool for the semi-automatic extraction of PV modules from thermographic UAV videos. We use it to curate a dataset containing 4.3 million IR images of 107842 PV modules from thermographic videos of seven different PV plants. To demonstrate its use for automated PV plant inspection, we train a ResNet-50 to classify ten common module anomalies with more than 90 % test accuracy. Experiments show that our tool generalizes well to different PV plants. It successfully extracts PV modules from 512 out of 561 plant rows. Failures are mostly due to an inappropriate UAV trajectory and erroneous module segmentation. Including all manual steps our tool enables inspection of 3.5 MWp to 9 MWp of PV installations per day, potentially scaling to multi-gigawatt plants due to its parallel nature. While we present an effective method for automated PV plant inspection, we are also confident that our approach helps to meet the growing demand for large thermographic datasets for machine learning tasks, such as power prediction or unsupervised defect identification.
</details>

[PDF (ArXiv)](/assets/documents/publication_1_arxiv.pdf) \| [PDF (Journal)](/assets/documents/publication_1_journal.pdf)

<h4 id="publication-2">[2] L. Bommes, M. Hoffmann, C. Buerhop-Lutz, T. Pickel, J. Hauch, C. Brabec, A. Maier, and I. Peters, “Anomaly detection in IR images of PV modules using supervised contrastive learning,” <em>Progress in Photovoltaics: Research and Applications</em>, vol. 30, no. 6, pp. 597–614, 2022. DOI: <a href="https://doi.org/10.1002/pip.3518">10.1002/pip.3518</a>.</h4>

<details style="margin-bottom: 10px;">
  <summary>Abstract</summary>
Increasing deployment of photovoltaic (PV) plants requires methods for automatic detection of faulty PV modules in modalities, such as infrared (IR) images. Recently, deep learning has become popular for this. However, related works typically sample train and test data from the same distribution ignoring the presence of domain shift between data of different PV plants. Instead, we frame fault detection as more realistic unsupervised domain adaptation problem where we train on labelled data of one source PV plant and make predictions on another target plant. We train a ResNet-34 convolutional neural network with a supervised contrastive loss, on top of which we employ a k-nearest neighbor classifier to detect anomalies. Our method achieves a satisfactory area under the receiver operating characteristic (AUROC) of 73.3 % to 96.6 % on nine combinations of four source and target datasets with 2.92 million IR images of which 8.5 % are anomalous. It even outperforms a binary cross-entropy classifier in some cases. With a fixed decision threshold this results in 79.4 % and 77.1 % correctly classified normal and anomalous images, respectively. Most misclassified anomalies are of low severity, such as hot diodes and small hot spots. Our method is insensitive to hyperparameter settings, converges quickly and reliably detects unknown types of anomalies making it well suited for practice. Possible uses are in automatic PV plant inspection systems or to streamline manual labelling of IR datasets by filtering out normal images. Furthermore, our work serves the community with a more realistic view on PV module fault detection using unsupervised domain adaptation to develop more performant methods with favorable generalization capabilities.
</details>

[PDF (ArXiv)](/assets/documents/publication_2_arxiv.pdf) \| [PDF (Journal)](/assets/documents/publication_2_journal.pdf)

<h4 id="publication-3">[3] L. Bommes, T. Pickel, C. Buerhop-Lutz, J. Hauch, C. Brabec, and I. Peters, “Georeferencing of photovoltaic modules from aerial infrared videos using structure-from-motion,” <em>Progress in Photovoltaics: Research and Applications</em>, vol. 30, no. 9, pp. 1122–1135, 2022. DOI: <a href="https://doi.org/10.1002/pip.3564">10.1002/pip.3564</a>.</h4>

<details style="margin-bottom: 10px;">
  <summary>Abstract</summary>
To identify abnormal photovoltaic (PV) modules in large-scale PV plants economically, drone-mounted infrared (IR) cameras and automated video processing algorithms are frequently used. While most related works focus on the detection of abnormal modules, little has been done to automatically localize those modules within the plant. In this work, we use incremental structure-from-motion to automatically obtain geocoordinates of all PV modules in a plant based on visual cues and the measured GPS trajectory of the drone. In addition, we extract multiple IR images of each PV module. Using our method, we successfully map 99.3 % of the 35084 modules in four large-scale and one rooftop plant and extract over 2.2 million module images. As compared to our previous work, extraction misses 18 times less modules (one in 140 modules as compared to one in eight). Furthermore, two or three plant rows can be processed simultaneously, increasing module throughput and reducing flight duration by a factor of 2.1 and 3.7, respectively. Comparison with an accurate orthophoto of one of the large-scale plants yields a root mean square error of the estimated module geocoordinates of 5.87 m and a relative error within each plant row of 0.22 m to 0.82 m. Finally, we use the module geocoordinates and extracted IR images to visualize distributions of module temperatures and anomaly predictions of a deep learning classifier on a map. While the temperature distribution helps to identify disconnected strings, we also find that its detection accuracy for module anomalies reaches, or even exceeds, that of a deep learning classifier for seven out of ten common anomaly types.
</details>

[PDF (ArXiv)](/assets/documents/publication_3_arxiv.pdf) \| [PDF (Journal)](/assets/documents/publication_3_journal.pdf)

<h4 id="publication-4">[4] L. Bommes, X. Lin, J. Zhou, “MVmed: Fast multi‑object tracking in the compressed domain,” <em>15th IEEE Conference on Industrial Electronics and Applications (ICIEA)</em>, 2020. DOI: <a href="https://doi.org/10.1109/ICIEA48937.2020.9248145">10.1109/ICIEA48937.2020.9248145</a>.</h4>

<details style="margin-bottom: 10px;">
  <summary>Abstract</summary>
We present MVmed, an algorithm for real-time online tracking of people and objects in MPEG-4 and H.264 compressed videos and integrate it into a multi-purpose tracking software for manufacturing sites. To support arbitrary video sources with no prior setup our tracker needs to be compatible with a variety of video codecs and camera settings. Existing compressed domain trackers are limited in this regard. They require a fixed interval of key frames, use only P frames and usually support only a single codec. MVmed overcomes these limitations and supports both MPEG-4 and H.264 codecs, P and B frames and arbitrary key frame intervals. On the MOT17 benchmark MVmed achieves a MOTA of 45.3 % at 42.1 Hz (266.9 Hz without detection) which is as accurate but significantly faster than the previous state of the art in compressed domain tracking. With this work we release the source code of MVmed and a Python package for motion vector extraction from video.
</details>
