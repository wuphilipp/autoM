---
title: Overview of System
order: 3
latex: yes
---

## Calibrations

We had to properly calibrate the location of our remover so that it correctly indexed to each printer

The procedure is uses a [tweaked version of the ar_track_alvar](https://github.com/brentyi/ar_track_alvar) ROS package, which allows our Sawyer's gripper camera and our Kinect's depth camera to each track a shared set of randomly placed AR tags.

![calibration photo](https://i.imgur.com/8h9M3ah.jpg)

Then, we try to find the optimal **world => Kinect** transformation, which minimizes the squared positional error between the two broadcasted tfs associated with each tag. If we define a matrix X whose rows are the positions of the tags in the Kinect frame and a matrix Y whose rows are the positions of these tags in the world frame, we can solve for the position and orientation of the Kinect as follows:

$$
\begin{align*}
    X &= \begin{bmatrix}\vec{x}_1 & \vec{x}_2 & \dots & \vec{x}_n\end{bmatrix}^T\\
    Y &= \begin{bmatrix}\vec{y}_1 & \vec{y}_2 & \dots & \vec{y}_n\end{bmatrix}^T\\
    R, t &= \text{argmin}_{R\in\textit{SO}(3), t\in\mathbb{R}^3}\sum||(Rx_i + t) - y_i||^2
\end{align*}
$$


## 3D Printed Gears 

Images of our gears

![marshmallow tfs](https://i.imgur.com/oOOaKOh.png?1)


![marshmallow flow chart](https://i.imgur.com/iaKP4Jt.png)

## Software Implmentation

We used a rasberry pi3 to control our system


![mouth tracking](https://i.imgur.com/EnqBAi0.jpg)

![gripper](https://i.imgur.com/7p8PIYj.jpg)

The gripping action is abstracted into the “grip” button on the web interface.



## Running our project
Thi is how we ran our project


Instead, we split our project up into several different logically grouped launch files. A [shell script](https://github.com/brentyi/marshmello_bringup/blob/master/run.sh) was then written to automatically launch each of them in named [tmux](https://github.com/tmux/tmux/wiki) panes. This was easy to run, yet also easy to debug:

```shell
tmux new-session -d -s marshmello

tmux rename-window 'sawyer'
tmux send-keys 'roslaunch marshmello_bringup sawyer_moveit.launch'

tmux new-window -t marshmello -n 'rviz'
tmux send-keys 'roslaunch marshmello_bringup sawyer_rviz.launch'

tmux new-window -t marshmello -n 'camera_drivers'
tmux send-keys 'roslaunch marshmello_bringup camera_drivers.launch'

...
```
