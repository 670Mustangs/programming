---
title: ODroid XU4
parent: Coprocessors, Sensors, and LEDs
grand_parent: 2019 Tech Binder
nav_order: 1
---

![ODroid](https://cdn.antratek.nl/media/product/d9e/odroid-xu4-octa-core-computer-with-samsung-exynos-5422-hk-odroid-xu4-47c.jpg)

The ODroid XU4 coprocessor is a powerful coprocessor for vision when you want a continuous feed for vision, such as if you were feeding its data directly into a PID loop. However, it is a large current draw, and not necessary if using the option we went for with vision this year: taking a single picture for targeting using a camera connected to a Raspberry Pi, then using a Pure Pursuit algorithm to drive to the target.

The way we chose to power it was to plug it directly into one of the 20 amp sections of the PDP, then step down the voltage using an adjustable power supply off of Amazon.

Beware that the ODroid seems to get extremely hot when running for an extended period. It has a fan for cooling, but make sure the case has holes in it and that it is not placed in an area with little air flow.

For a good metric of power of the Odroid compared to the Raspberry Pi, [check out the Liger Bots white paper which we used as a reference](https://www.chiefdelphi.com/t/a-step-by-step-run-through-of-frc-vision-processing/341012). 