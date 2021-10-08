## Introduction
This is a gazebo based pipeline to generate simnulated rgb/depth images for creating datasets for deep learning tasks. A Kinect camera is simulated around the origin of the world according to a pre-defined algorithm and images are captured and saved.

## Installation
1. Create a catkin_ws in your working directory :
    ~~~
    $ mkdir -p ~/catrkin_ws/src
    ~~~
2. Clone the repo into your src folder :
    ~~~
    $ cd catkin_ws/src
    $ git clone --branch object_classification https://github.com/KulunuOS/gazebo_dataset_generation.git
    ~~~

3. Build the workspace
    ~~~
    $ cd ..
    $ catkin_make
    ~~~
4. roslaunch the world
    ~~~
    $ source devel/setup.bash 
    $ roslaunch data_generation metrics.launch
    ~~~ 
5. Install requirements and activate conda environment
    ~~~
    $ cd src
    $ conda env create -f env.yml
    ~~~

6. modify the sdf files,world file , include new nesh files and re launch
    
    Include the mesh file, model.sdf, model.config files of your dataset in data_generation/models folder
    
    Include the objects in data_generation/Worlds/metrics.world file according to preference:

    An example of loading the object 'left_gear' on to the table is as below
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
