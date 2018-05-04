---
title: Software
order: 9
latex: yes
---

## This is how you run our project!
- [Code base for the AutoM](https://github.com/phil80301/automated_3dprinter)
- [This Website](https://github.com/phil80301/autoM)
## This is how you calibrate our project!
You need to calibrate the AutoM by insuring that the print remover properly lines up with each respective printer. You also may need to adjust the 8020 bolts in the back of the rail to calibrate the remover z height. You can run the calibration script which lets you do just that!
First make sure you power cycle all of the printers, waiting a few seconds before turning them back on.
```shell
python -i control_all.py
>>> mf(1) # move remover to printer 1 and index
>>> mf(3) # move remover to printer 3 and index
>>> mr(2) # execute full removal sequence on printer 2
>>> mr(4) # execute full removal sequence on printer 4
```

Once you are satisfied with the removers indexing performance, you can now run prints! See the software section below for more details.
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

