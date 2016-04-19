- - - - - - - - - - 
install and setup ros
- - - - - - - -- - 

 * sudo apt-get install ros-jade-desktop-full
 * sudo rosdep init

rosdep update

echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc

source ~/.bashrc

sudo apt-get install python-rosinstall
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
catkin_init_workspace
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc

- - - - - - - - - - 
     BUILD
- - - - - - - - - - 
catkin_make --pkg paexample

- - - - - - - - - - 
      RUN
- - - - - - - - - - 
roslaunch paexample paexample.launch

Feature extraction and train:
rosrun paexample features_subscriber.py addClass silence
rosrun paexample features_subscriber.py addClass speech
rosrun paexample features_subscriber.py addClass music
rosrun paexample features_subscriber.py addClass activity
rosrun paexample features_subscriber.py train model1 silence.npy speech.npy music.npy activity.npy 


- - - - - - - -
 Requirements
- - - - - - - -
a) fftw: 
sudo apt-get install libfftw3-dev 

b) portaudio:
sudo apt-get install libjack-jackd2-dev
sudo apt-get install portaudio19-dev
sudo apt-get install libportaudiocpp0

c) boost

d) sndfile:
sudo apt-get install libsndfile1-dev 

e) eigen3:
sudo apt-get install libeigen3-dev

f) Based on your Ubuntu version, select the correct ROS distribution. For example, for Ubuntu 14 use (ROS Indigo):
http://wiki.ros.org/indigo/Installation/Ubuntu
For Ubuntu 15 use (ROS Jade):
http://wiki.ros.org/jade/Installation/Ubuntu


- - - - - - - - - - 
Instructions regarding ROS: (applicable for any ROS package)
- - - - - - - -- - 

In order to compile this package you need to:

1. Create a catkin workspace:
http://wiki.ros.org/catkin/Tutorials/create_a_workspace
2. Compile the package by running (in the root of the workspace):
	catkin_make --pkg [name_of_package]
	to compile a spicific package or
	catkin_make
	to compile all packages inside the workspace.

In order to run this package you need to:

1. Add your workspace in your bashrc by adding this line to your bashrc:
export /path/to/your/workspace/devel/setup.bash
2. Source your bashrc (source ~/.bashrc) from your current terminal, or simply open a new one.
3. You can now run the package's executables by running:
	3.1. On one terminal run:
		roscore
	3.2. On another terminal run your executables by ruuning:
		rosrun paexample [name of the executable]
4. To run the main paexample executable, you should run (no need to run roscore on a separate terminal):
		roslaunch paexample paexample.launch

---
TIP: Use [TAB]'s autocomplete function
---


- - - - - - - - - - 
    USAGE MODES
- - - - - - - -- - 

In order to run the different modes of the paexample, use the parameters.yaml file under the config folder.
