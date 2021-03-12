# Detectron2 Object Detector for ROS

A ROS Node for detecting objects using [Detectron2](https://github.com/facebookresearch/detectron2).


## Installation

It is necessary to install Detectron2 [requirements](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md) in a python *virtual environment* as it requires `Python 3.6` and ROS works with `Python 2.7`

1. Install python Virtual Environment
```bash
sudo apt-get install python-pip
sudo pip install virtualenv
mkdir ~/.virtualenvs
sudo pip install virtualenvwrapper
export WORKON_HOME=~/.virtualenvs
echo '. /usr/local/bin/virtualenvwrapper.sh' >> ~/.bashrc 
```

2. Creating Virtual Environment
```bash
mkvirtualenv --python=python3 detectron2_ros
```

3. [Install the dependencies in the virtual environment](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md)

```bash
pip install -U torch==1.4+cu100 torchvision==0.5+cu100 -f https://download.pytorch.org/whl/torch_stable.html
pip install cython pyyaml==5.1
pip install -U 'git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cu100/index.html
pip install opencv-python
pip install rospkg
```


## Downloading the Package

3. Clone the package to the ROS workspace using git tools
```bash
git clone https://github.com/DavidFernandezChaves/detectron2_ros.git
cd detectron2_ros
git pull --all
git submodule update --init
```

## Compilation

4. Attention: DO NOT USE the python virtual environment previously built to compile catking packages.
```bash
catkin_make
source $HOME/.bashrc
```

## Running

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

The following arguments can be set on the `roslaunch` above.
- `input`: image topic name
- `detection_threshold`: threshold to filter the detection results [0, 1]
- `visualization`: True or False to pubish the result like a image
- `model`: path to the training model file. For example: `/detectron2/configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml`

## Citing Detectron
If you use Detectron2 in your research or wish to refer to the baseline results published in the Model Zoo, please use the following BibTeX entry.

```bash
@misc{wu2019detectron2,
  author =       {Yuxin Wu and Alexander Kirillov and Francisco Massa and
                  Wan-Yen Lo and Ross Girshick},
  title =        {Detectron2},
  howpublished = {\url{https://github.com/facebookresearch/detectron2}},
  year =         {2019}
}
```
