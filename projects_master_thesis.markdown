---
layout: page
title: Multi-camera Tracking System for Shopfloor Monitoring (Master’s Thesis)
permalink: /projects/master_thesis/
---

*Conducted during*: Master thesis at IWF TU Braunschweig and A*Star SIMTech Singapore / Software Engineer at A*Star SIMTech

*Topic*: Development of a multi-camera-based detection and tracking system for shopfloor monitoring

**Motivation**: Despite a high degree of automation many manufacturing processes incorporate human workers because of their superior flexibility and ability to conduct complex tasks. Monitoring of human workers is an important cornerstone for more informative digital factory models, which do not only include machine- and operations-related data, but also the state of the human work force. This can reduce human errors and improve product quality as well as work safety.

**Aim**: Develop a software system which tracks human workers (and other objects) with multiple surveillance cameras in a factory environment.

**Method**: Video streams of multiple network surveillance cameras are captured and synchronized. People and objects are detected with a Faster R-CNN model in regular intervals and tracked in intermediate frames using the fast [MVmed multi-object tracker](#mvmed-tracker). Locations of people within different cameras are fused and mapped to the factory floor by means of homography transformations, which are determined a priori via camera calibration. Tracked people and objects are visualized in real-time in a web app containing a virtual 2D floorplan (see fig. 1). Furthermore, trajectories are persisted, enabling different types of analyses, e.g., to reduce walking distances in a manufacturing process.

![shopfloor_monitor_overview](/assets/projects/images/shopfloor_monitor.png)
*Fig. 1: Components of the Shopfloor Monitor: two out of seven video streams with tracked people (left) and the web app with virtual 2D floorplan (right).*

**Practical Relevance**: The Shopfloor Monitor is deployed in the Model Factory at SIMTech and in active development. During my time at SIMTech the project received interest from an international hotel chain for smart control of HVAC and lighting systems. Several interns have contributed to the project. One of them extended the Shopfloor Monitor to ensure workers wear mandatory safety gear. Currently, the Shopfloor Monitor is modified to monitor social distancing during the Covid-19 pandemic in Singapore. Apart from this, the Shopfloor Monitor also received negative feedback for being potentially intrusive to workers’ privacy.

## Software

### Shopfloor Monitor (unpublished)

*Description*: The Shopfloor Monitor is a proprietary software in active development at A*Star SIMTech.

*Technologies*: The Shopfloor Monitor comprises of a command line tool written in Python, which contains the application logic, and a web app based on Python Flask for visualization of tracked people in real-time on a virtual 2D floorplan. The floorplan is based on SVG, D3.js, and three.js. Apache ECharts are used for real-time display of statistics. Communication between backend and frontend is realized with sockets. The web app is served with NGINX and a MongoDB is used for data storage. Deep learning components are implemented in Tensorflow 1. Docker and Docker Compose are used for the deployment of the system, which is implemented in a microservice pattern. Several extension modules have been developed: The [RTSP Video Stream Synchronizer](#rtsp-video-stream-synchronizer) for synchronization of the network camera streams, and the [MVmed tracker](#mvmed-tracker) for fast multi-object tracking based on motion vector fields contained in the encoded video streams. These motion vector fields are extracted with the [Motion Vector Extractor](#motion-vector-extractor).

### RTSP Video Stream Synchronizer

*GitHub*: https://github.com/LukasBommes/rtsp-streamsync

*Description*: The Shopfloor Monitor relies on the video input of multiple network video cameras, which, by default, are not synchronized and exhibit stream offsets of tens of seconds. To solve this issue, I developed the RTSP Video Stream Synchronizer, which is a C++/Python library for the synchronization of video frames from multiple network network cameras. In tests, the algorithm synchronized seven parallel video streams with an initial offset of 28.7 seconds to an accuracy of 50.5 milliseconds in real-time.

### Motion Vector Extractor

*GitHub*: https://github.com/LukasBommes/mv-extractor

*Description*: A tool for the extraction of motion vector fields (see fig. 2) from H.264 and MPEG-4 Part 2 encoded video streams (see [publication [4]](/publications#publication-4) for details). Extracted motion vectors can be used for downstream tasks, such as object detection, object tracking, structure from motion, or video stabilization. Since motion vectors are readily available in the video stream, no additional computation is needed to estimate scene motion. This is a great advantage over techniques operating on the decoded frames, such as optical flow.

![mv_extractor](/assets/projects/images/mv_extractor.png)
*Fig. 2: Exemplary video frame with motion vectors extracted by the motion vector extractor.*

*Technologies*: The tool exposes a single class acting as a drop-in replacement for OpenCV’s VideoCapture class. In addition to the decoded frame, motion vectors and the type of each frame (I/P/B frame) are returned. FFMPEG is used for handling of the video stream, decoding of frames and unpacking of motion vectors. The Python and Numpy C APIs are utilized to provide a Python wrapper around the C++ API.

### MVmed Tracker

*GitHub*: https://github.com/LukasBommes/mvmed-tracker

*Description*: MVmed tracker is a real-time online multi-object tracker for videos, which exploits motion vector fields readily available in MPEG-4 or H.264 encoded video streams to achieve very high tracking speeds (see [publication [4]](/publications#publication-4) for details). The tracker uses a Faster R-CNN to detect object bounding boxes in regular intervals, which are propagated by averaging of the motion vector field inside the box (see fig. 3). On the MOT17 benchmark MVmed achieves a MOTA of 45.3 % at 42.1 Hz (266.9 Hz without detection), which is as accurate but much faster than the previous state of the art tracker for encoded videos.

![mvmed_tracker](/assets/projects/images/mvmed_tracker.png)
*Fig. 3: Exemplary output of the MVmed tracker. Red arrows indicate the motion vector field. Detected and tracked bounding boxes are shown in blue and orange, respectively.*

*Technologies*: The tracking algorithm is implemented in pure Python and the motion vector field is extracted with the [Motion Vector Extractor](#motion-vector-extractor). I used the Faster R-CNN model provided in the Tensorflow object detection API.

*Note*: I also experimented about two months with a convolutional neural network for motion prediction from the motion vector field but could not achieve the performance of the simple median averaging performed in MVmed.

## Related Publications

The following conference paper was published during this project: [[4]](/publications#publication-4)

