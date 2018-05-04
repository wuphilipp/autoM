---
title: Calibration 
order: 8
latex: yes
---

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
