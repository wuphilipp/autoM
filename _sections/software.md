---
title: Software
order: 9
latex: yes
---

## This is how you run our project!
## Software Implmentation

We used a Rasberry Pi 3 to control our system.
In addition we have 4 Monoprice Mini printers which connect to our system.
Lastly two arduinos control the actuators of our system, which the Rasberry Pi also interfaces to.

## Setting up the printers
First load the gcode files you wish to print on all the 3D printers.
Then make sure to restart all of the printers, waiting a few second before turning them back on.

## Making a print queue
First you will need to enter the automated_3dprinting folder on the pi. You will then need to edit the print que with your prints. Edit the file print_que.txt using the text editor of your choice so that it includes the prints you want. You will need one line per gcode file.
```shell
cd automated_3dprinter
vim print_que.txt
```

## Starting Prints
Now you just need to run the main.py file which will start the prints!
We run sudo because there are keyboard interrupt function which you can take advantage of if you want to remove prints early.
```shell
sudo python main.py
```
Now you've fully automated your 3D Printing system!
