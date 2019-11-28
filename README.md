# Detectron2 Object Detector for ROS
---
A ROS Node for detecting objects using [Detectron2](https://github.com/facebookresearch/detectron2).


## Installation
----
It is necessary to install Detectron2 [requirements](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md) in a python *virtual environment* as it requires `Python 3.6` and ROS works with `Python 2.7`

1. Install python Virtual Environment
```bash
$ sudo pip install virtualenv
$ sudo pip install virtualenvwrapper
```

2. Creating Virtual Environment
```bash
$ venv_name=detectron2_ros
$ mkvirtualenv --python=python3 $venv_name
```

[Install the dependencies](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md)


## Downloading the Package
---
3. Clone the package to the ROS workspace using git tools
```bash
$ git clone https://github.com/DavidFernandezChaves/detectron2_ros.git
$ cd detectron2_ros
$ git pull --all
$ git submodule update --init
```

## Compilation
------------
4. Attention: DO NOT USE the python virtual environment previously built to compile catking packages.
```bash
  $ catkin_make
  $ source $HOME/.bashrc
```

## Running
---
1. First launch ROScore into a terminal.

2. Next, open a new terminal and use the virtual environment created.
```bash
workon detectron2_ros
```
3. Running the node
```bash
roslaunch detectron2_ros detectron2_ros.launch
```

## Arguments
---
The following arguments can be set on the `roslaunch` above.
- `input`: image topic name
- `detection_threshold`: threshold to filter the detection results [0, 1]
- `model`: path to the training model file. For example: `/detectron2/configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml`
