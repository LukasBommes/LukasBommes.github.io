---
layout: page
title: Control System for a Thermal Micromachining Workpiece Clamp (Bachelor’s Thesis)
permalink: /projects/bachelor_thesis/
---

*Conducted during*: Bachelor thesis at IWF TU Braunschweig

*Topic*: Development of a control system for clamping of workpieces by adhesion forces in micromachining

**Method**: In this project I developed the controller of a thermal workpiece clamp for micromachining (see fig. 1). The clamp uses a thermoelectric cooler/heater (TEC) to fixate small workpieces either by freezing of water or melting and solidifying of wax. I designed and produced the driver electronics for the TEC and modelled and simulated the thermoelectric behavior of the system (physically and experimentally by measuring the step response). Based on the model I designed, simulated, and tuned a PI temperature controller. I implemented the temperature controller in C++ on an Atmel 8-bit microcontroller in addition to the control logic and an interface for communication with a PC. To control the clamp via a PC, I developed an application-specific protocol and built a graphical user interface with MATLAB (see fig. 2).


![thermal_workpiece_clamp](/assets/projects/images/thermal_workpiece_clamp.png)
*Fig. 1: CAD model of the thermal components of the work piece clamp (left) and the manufactured clamp with casing (right).*

![workpiece_clamp_gui](/assets/projects/images/workpiece_clamp_gui.png)
*Fig. 2: MATLAB-based graphical user interface for controlling the thermal workpiece clamp.*
