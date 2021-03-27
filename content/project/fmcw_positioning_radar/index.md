---
title: FMCW Positioning Radar

# Summary for listings and search engines
summary: A FMCW Radar with 4 transmitting antennas and 12 receive antennas working within the 2.7 GHz - 3.7 GHz band that can locate a person in the same room with accuracy of 20 cm.

tags:
- Radar

# Date published
date: "2018-05-28T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: The whole system on a cart
  focal_point: Smart
  preview_only: false

# links:
# - icon: twitter
#   icon_pack: fab
#   name: Follow
#   url: https://twitter.com/georgecushen
url_code: "https://github.com/pidan1231239/fmcw_positioning_radar"
url_pdf: ""
url_slides: "https://sway.office.com/5uSW86N1bUqbrA7T?ref=Link"
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

## Introduction

FMCW Positioning Radar project is a work of team made up of three people. We were trying to get the qualification to attend [ESDC](http://nuedc.sjtu.edu.cn/CN/content.aspx?info_lb=37&flag=2) through this project. Sadly, we were out of the game in the stage of school contest.
The radar works in the 2.7 GHz - 3.7 GHz band. It has 4 transmitting antenna and 12 receive antenna. With a transmission power of less than 10 dBm, it localizes a person within a median of 5 cm in the y dimension. Within 5 meters, it has an accuracy of about 20 cm. Without further tests, the maximum distance is unknown. However, it can indicate a person behind a 25 cm concrete wall.
Code and document [here](https://github.com/pidan1231239/fmcw_positioning_radar). The final presentation with hardware and data processing flow introduction see [here](https://sway.com/5uSW86N1bUqbrA7T?ref=Link).

### FMCW

> Frequency-modulated continuous-wave radar (FM-CW) – also called continuous-wave frequency-modulated (CWFM) radar – is a short-range measuring radar set capable of determining distance ([Continuous-wave radar wiki](https://en.wikipedia.org/wiki/Continuous-wave_radar)). 

If you have no idea about it, the tutorial below is a good starting point.
- [Frequency-Modulated Continuous-Wave Radar](http://www.radartutorial.eu/02.basics/Frequency%20Modulated%20Continuous%20Wave%20Radar.en.html) ([FMCW Radar](http://www.radartutorial.eu/02.basics/Frequency%20Modulated%20Continuous%20Wave%20Radar.en.html)): a brief introduction of the principle of FMCW
- [Build a Small Radar System Capable of Sensing Range, Doppler, and Synthetic Aperture Radar Imaging](https://ocw.mit.edu/resources/res-ll-003-build-a-small-radar-system-capable-of-sensing-range-doppler-and-synthetic-aperture-radar-imaging-january-iap-2011/index.htm): an MIT course to build an FMCW radar yourself
- [GUEST POST: TRY RADAR FOR YOUR NEXT PROJECT](https://hackaday.com/2014/02/24/guest-post-try-radar-for-your-next-project/): an article written by the instructor of the course above
- [Intro to mmWave Sensing: FMCW Radars - Module 1: Range Estimation](https://training.ti.com/intro-mmwave-sensing-fmcw-radars-module-1-range-estimation): a series of 5 short videos  providing a concise yet in-depth introduction to sensing using FMCW radars

### SDR

> [Software-defined radio](https://en.wikipedia.org/wiki/Software-defined_radio) (SDR) is a radio communication system where components that have been traditionally implemented in hardware (e.g. mixers, filters, amplifiers, modulators/demodulators, detectors, etc.) are instead implemented by means of software on a personal computer or embedded system.

The project uses a USRP N210 with an LFRX  daughter board. SDR is not an important part of this project cause the RF front end are made with RF modules and the FMCW generator is build separately. The USRP here acts as a role of ADC and is accessed via Simulink. See how to use a USRP with Simulink below:
- [USRP® Support Package from Communications System Toolbox](https://ww2.mathworks.cn/hardware-support/usrp.html?s_tid=srchtitle): Matlab toolbox for USRP
- [Digital Communication Systems Engineering Using Software Defined Radio](http://ecewp.ece.wpi.edu/wordpress/wireless/textbooks/sdrlabs/): a tutorial of SDR using Simulink


## Hardware

The hardware design can be introduced in two parts, RF front end and FMCW generator. The design references the projects and the papers below:
- [Build a Small Radar System Capable of Sensing Range, Doppler, and Synthetic Aperture Radar Imaging](https://ocw.mit.edu/resources/res-ll-003-build-a-small-radar-system-capable-of-sensing-range-doppler-and-synthetic-aperture-radar-imaging-january-iap-2011/index.htm)
- [RF-Capture](http://rfcapture.csail.mit.edu/): [paper see RF-Capture: Capturing a Coarse Human Figure Through a Wall](http://rfcapture.csail.mit.edu/rfcapture-paper.pdf)
- [WiTrack](http://witrack.csail.mit.edu/): papers see [3D Tracking via Body Radio Reflections](http://witrack.csail.mit.edu/witrack-paper.pdf), [Multi-Person Localization via RF Body Reflections](http://witrack.csail.mit.edu/witrack2-paper.pdf)

### FMCW generator
- [ADF4159](http://www.analog.com/en/products/clock-and-timing/phase-locked-loop/fractional-n-pll/adf4159.html) evaluation board: [EV-ADF4159EB3Z](http://www.analog.com/en/design-center/evaluation-hardware-and-software/evaluation-boards-kits/eval-adf4159.html)
- Loop filter: [AD8065](http://www.analog.com/cn/products/amplifiers/operational-amplifiers/jfet-input-amplifiers/ad8065.html). It is designed with [ADIsimPLL](https://form.analog.com/Form_Pages/RFComms/ADISimPll.aspx) under the guidance of [CN-0302](http://www.analog.com/media/en/reference-design-documentation/reference-designs/CN0302.pdf).
- VCO: [ZX95-3800A+](https://www.minicircuits.com/WebStore/modelSearch.html?model=ZX95-3800A%2B)
- Power splitter: [ZX10-2-42+](https://www.minicircuits.com/WebStore/modelSearch.html?model=ZX10-2-42%2B)
- Attenuator: [VAT-3+](https://www.minicircuits.com/WebStore/modelSearch.html?model=VAT-3%2B)

The final design works in 2.7 GHz to 3.7 GHz to avoid 2.4 GHz band.

{{< figure src="FMCW信号发生.png" caption="FMCW generator" >}}

### RF front end
- PA and LNA: [ZX60-53LNB+](https://www.minicircuits.com/WebStore/modelSearch.html?model=ZX60-53LNB%2B)
- Power splitter: [ZN2PD-9G+](https://www.minicircuits.com/WebStore/modelSearch.html?model=ZN2PD-9G%2B)
- Attenuator: [FW-9+](https://www.minicircuits.com/WebStore/modelSearch.html?model=FW-9%2B)
- Mixer: [ZX05-43+](https://www.minicircuits.com/WebStore/modelSearch.html?model=ZX05-43%2B)
- Switch: ADRF5040
- mbed board: ST NUCLEO-L476RG

The mbed board detects the trigger edge and overlay current antenna pair number after the edge. The baseband signal from the mixer and coded sync signal from mbed board are sent into the same LFRX board to achieve synchronization, then will be analyzed in Simulink in real time.

{{< figure src="FMCW射频前端.png" caption="RF front end" >}}

## Software

Software part includes ADF4159 evaluation board configuration, mbed code, and Simulink model. 

### ADF4159

The ADF4159 evaluation board is configured using [ADF4158 and ADF4159 Evaluation Board Software](http://www.analog.com/media/en/evaluation-boards-kits/evaluation-software/ADF4158-9_Setup_v4_10_6.zip) via USB. The configuration file [here](https://github.com/pidan1231239/fmcw_positioning_radar/tree/master/ad4159) can be loaded into the software. The board is configured as follows:
- Ramp mode: Continuous sawtooth
- RF frequency: 2.7 GHz - 3.7 GHz
- Ramp frequency: 2000 Hz
- Charge pump: 1.25 mA
- Muxout: Digital lock Detect. It is used as a sync signal to trigger the switching of antennas.

The 4 Tx and 12 Rx makes up 4*12 antenna pairs. With ramp frequency of 2000 Hz, every antenna pair is switched to for 41.7 times per second.

### mbed code

The mbed board switches antenna pairs after every trigger edge from the ADF4159 Muxout pin. And it also overlay the antenna pair number to the sync signal. Considering that MCU has some unstable reaction delay between the trigger edge of the sync signal and the first down edge of the output, the MCU first pulls down the sync signal then output bits of the number. In this way, the down edge of the overlaid signal has no jitter. Code of mbed board is [here](https://github.com/pidan1231239/fmcw_positioning_radar/tree/master/mcu).

{{< figure src="IMG_20180623_094926.jpg" caption="Antenna switching timing diagram" >}}

### Simulink model

All the models are in the [simulink](https://github.com/pidan1231239/fmcw_positioning_radar/tree/master/simulink) folder. [RadarImagingAndPositioning.slx](https://github.com/pidan1231239/fmcw_positioning_radar/blob/master/simulink/RadarImagingAndPositioning.slx) block implements the basic signal processing logic and output the 2D heat map and target position. The data processing flow is shown in the presentation above. [usrp_4t12r_heatmap.slx](https://github.com/pidan1231239/fmcw_positioning_radar/blob/master/simulink/usrp_4t12r_heatmap.slx)  connects the basic blocks to show the imaging result and targets. For more information about using USRP with Simulink, see the Introduction section above.

## Results

In the experimental stage, I built a system with 1 Tx and 3 Rx.

{{< figure src="IMG_20180131_161431.jpg" caption="1TX3RX system" >}}

The overlaid sync signal is shown below.

{{< figure src="IMG_20180131_103642.jpg" caption="Sync signal" >}}

1D imaging of each antenna pair is shown below. Tested with a person walking away then walking back. The d axis shows the round trip of the radar signal.

{{< figure src="三根天线瀑布图.jpg" caption="1d imaging of each antenna pair" >}}

The system was then expanded to 1 Tx and 8 Rx. In this stage, 2D imaging can be done.

{{< figure src="IMG_20180205_100729.jpg" caption="1TX8RX system" >}}

The following image is the heat map captured from the 1Tx8Rx system. The x-axis indicates angle from left to right. y-axis indicates the round distance of the radar signal. This illustration was made in a hurry so there is no complete annotation.

{{< figure src="Image.png" caption="1Tx8Rx top-down heatmap" >}}

After that, the system was expanded to 4 Tx and 12 Rx. In this stage, 3D imaging can be done.

{{< figure src="1522473970150_48c5a36482b4463d3e4516373d3e01c5.jpg" caption="4TX12RX system" >}}

The following gif shows the 3D imaging projected to xz-plane of a person holding a corner reflector and drawing a circle in the air.

{{< figure src="yLoCut_200kHz_800rps_1rpf_4t12r_ztest_circle_reflector.gif" caption="Heatmap front view" >}}

The gif below shows the 2D imaging of xy-plane with target tracking. The target person was walking around in the distance of 3 meters. The y-axis indicates the round distance of radar signal.

{{< figure src="heatMapTarget.gif" caption="Heatmap top-down view" >}}

I tried to extract the z-axis coordinate of person target. However, because of the reflection angle mentioned in [RF-Capture](http://rfcapture.csail.mit.edu/), and the intensified effect by the lower frequency band of our system, the height of a person cannot be accurately detected. 
The image shows the heat map of the target in the z-axis changing with time. The target is walking in place then squats in the 10th second. As shown below, the height drops several times when the target moves.

{{< figure src="Image2.png" caption="Heatmap z" >}}

The final work was put on a cart.

{{< figure src="IMG_20180416_155121.jpg" caption="Final system" >}}
