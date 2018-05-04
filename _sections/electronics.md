---
title: Electronics
order: 8
latex: yes
---

## Overall Design

We chose to use two separate Arduinos to control the gripper and winch, due to the large distance between the two and their motion relative to each other. Having the Arduinos close to the motors they control minimizes voltage drop and the total amount of wiring. All circuits were assembled on perfboard for robustness.

![shelf]({{ "/assets/electronic.jpg" | absolute_url }})
## Gripper Electronics

The bed gripper is actuated by two Futaba 3003 servos controlled by an Arduino Nano. The Arduino receives commands from the Raspberry Pi (clamping, flexing, releasing) and sends PWM signals to the servos. Power and USB cables for the gripper electronics are routed through a cable carrier ("energy chain") to avoid tangling as the gripper moves up and down.

We burned out our first two servos by powering them with 12V. This issue was fixed by adding a 5V switching voltage regulator.

## Winch Electronics

The bed gripper is raised and lowered by a stepper motor, which is controlled by another Arduino Nano. The Arduino moves the bed gripper to the desired level using feedback from a limit switch. The limit switch is triggered by a screw at each level, which allows for fine tuning.

We chose to use a limit switch rather than open loop positioning, because the string stretches slightly under tension.
