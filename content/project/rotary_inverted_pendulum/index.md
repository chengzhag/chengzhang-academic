---
title: Rotary Inverted Pendulum

# Summary for listings and search engines
summary: A rotary inverted pendulum system built with an encoder, a brush motor, a STM32F103 board that is capable of setting target orientation, non-stop swinging and automatically swinging up.

tags:
- Contest
- Control System
- Electronics Design

# Date published
date: "2017-04-09T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: The whole system on a tripod
  focal_point: Smart
  preview_only: false

# links:
# - icon: twitter
#   icon_pack: fab
#   name: Follow
#   url: https://twitter.com/georgecushen
url_code: "https://github.com/pidan1231239/inverted_pendulum"
url_pdf: ""
url_slides: ""
url_video: "https://www.youtube.com/watch?v=R4VLmF_X5qM"

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

## Introduction

Rotary Inverted Pendulum is built with an encoder, a brush motor, a STM32F103 board. No rotation limit. Capable of setting target angle, non-stop swinging and automatically swinging up.

Rotary Inverted Pendulum project is a work of team. The other two teammates are [shicaiwei123](https://github.com/shicaiwei123) and [yoyolalala](https://github.com/yoyolalala). 

Code and document [here](https://github.com/pidan1231239/inverted_pendulum). Platform details [here]().

## Demo

Primary demo with very limited precision and robustness is shown below.

{{< youtube R4VLmF_X5qM >}}

## Mechanical structure

I use an optical encoder to measure the angle of the pendulum. The absolute angle of the pendulum need calibrate every time after reset.

{{< figure src="IMG_20170409_204205.jpg" caption="Optical encoder" >}}

A slip ring is used to prevent the winding of the wire.

{{< figure src="稿定设计导出-20180604-225745.jpg" caption="Slip ring" >}}

The DC brush motor with gearbox and magnetic encoder is driven by a TB6612FNG model controlled with PWM signal. A 3s lithium battery powers the system like the following projects.

{{< figure src="IMG_20170504_112659.jpg" caption="Complete circuit board" >}}

The mechanical structure includes three round mounting plates to mount slip ring, motor, and quick-release plate. The plates are connected with hexagonal copper pillars. The whole structure is mounted to a tripod through the quick-release plate. 

The round plates are rendered as acrylic plate below. But they are made of carbon fiber in the final work.

{{< figure src="Snipaste_2018-06-05_07-40-03.png" caption="The core mechanical structure" >}}

{{< figure src="84C~Z{NZ1N42UWZE8$K2QQ9.png" caption="The complete mechanical structure" >}}

## Software design

> Please refer to [Study on PID Control of a Single Inverted Pendulum System](http://en.cnki.com.cn/Article_en/CJFDTOTAL-JZDF2007S1010.htm) for the PID control system.
> {{< figure src="S$$(M)IHI`GJ)_%$CIG[MO0.png" caption="PID control system" >}}

> Also we refer to [Research and Implementation of the Swing - up and Stabilizing Operation for Rotational Inverted Pendulum](http://www.ahkjwx.cn:81/article/detail.aspx?id=669914934) for the swing-up and stabilizing operation.
> {{< figure src="A)$0J)GGY_]VH@}9J52[1HD.png" caption="Swing - up and stabilizing operation" >}}

The swing-up and stabilizing operation and the changes between different modes are modeled as a state machine.

{{< figure src="倒立摆状态机.png" caption="State machine for swing-up and stabilizing operation" >}}
