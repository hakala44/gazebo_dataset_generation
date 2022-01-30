## Robotics project work

This repository is forked from https://github.com/KulunuOS/gazebo_dataset_generation

All modifications are done for the needs of Diesel engine part dataset generation

## Automatic Dataset Generation From CAD for Vision Based Grasping

This is the official source code for Automatic Dataset Generation From CAD for Vision-Based Grasping, ICAR, 2021.

PDF: https://research.tuni.fi/uploads/2021/10/5f29a62c-icar_2021_dataset.pdf


[![Automatic Dataset Generation From CAD for Vision Based Grasping HD](https://res.cloudinary.com/marcomontalbano/image/upload/v1634114596/video_to_markdown/images/youtube--DwlWrxc3Wis-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=DwlWrxc3Wis "Automatic Dataset Generation From CAD for Vision Based Grasping HD")


## Requirements

- Ubuntu 20.04 and ROS Noetic
- Gazebo multi-robot simulator, version 11.5.1
- Anaconda distribution 
- Python 3.6 

## Installation
1. Create a catkin_ws in your working directory :
    ~~~
    $ mkdir -p ~/catkin_ws/src
    ~~~
2. Clone the repo into your src folder :
    ~~~
    $ cd catkin_ws/src
    $ git clone https://github.com/KulunuOS/gazebo_dataset_generation.git .
    ~~~

3. Build the workspace
    ~~~
    $ cd ..
    $ catkin_make
    ~~~
4. roslaunch the gazebo world
    ~~~
    $ source devel/setup.bash 
    $ roslaunch data_generation metrics.launch
    ~~~ 
5. Install dependencies and activate conda environment. ( you need to have anaconda installed and configured )
    ~~~
    $ cd src
    $ conda env create -f env.yml
    $ conda activate open3d
    ~~~

6. Ḿodify the gazebo world according to the preference of your dataset.
    
    Include the mesh files, model.sdf, model.config files of the objects in your dataset in data_generation/models folder
    
    Include the following in data_generation/Worlds/metrics.world file according to preference

    An example of loading the object 'left_gear' on to the table is as below :
    ~~~
    <include>
      <uri>model://left_gear</uri>
      <name>left_gear</name>
      <pose>0 0 0.84 0 0 0</pose>
    </include> 
    ~~~


## Data Generation

1. launch the gazebo world again as in step 4 and check if the objects are placed according to your preference.

2. Run the generating script in a seperate terminal in parallel with gazebo world launched previously  
    ~~~
    $ cd ~/data_generation/gen_script                          
    $ python render.py models <link_name>
    ~~~
3. The rgb and depth files will be saved to /data_generation/gen_script directory in the folders /rgb and /depth respectively

## Acknowledgement

Project funding was received from European Union's Horizon 2020 research and innovation programme, grant agreement no. 871252 (METRICS) and no. 871449 (OpenDR), and from Helsinki Institute of Physics' Technology Programme (project; ROBOT). The authors wish to acknowledge CSC - IT Center for Science, Finland, for computational resources.

## Citations

Please cite the work if you use this repository in your publications:
```
@InProceedings{Saad_2021_ICAR,
author = {Saad Ahmad, Kulunu Samarawickrama, Esa Rahtu and Roel Pieters},
title = {Automatic Dataset Generation From CAD for Vision Based Grasping},
booktitle = {20th International Conference on Advanced Robotics (ICAR)},
month = {December},
year = {2021}
}
```
