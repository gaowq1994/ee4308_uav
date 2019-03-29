# EE4308 - Advances in Intelligent Systems and Robotics - Part 2 Project - NUS 2019 #
------------------------------
UAV Path Planning and Navigation. The aim of this project is to navigate the UAV autonomously from point A (x,y) = (-1.5,1.5) to point C (x,y) = (-1.5,-1.5) through point B (x,y) = (2,0), in a 6m x 6m x 2m room equipped with cameras for UAV position estimation.

The project is part of the assessment in the second half of the course EE4308: Advances in Intelligent Systems and Robotics taught at the National University of Singapore (NUS) during Semester 2 of AY2018/19. 


## Software Tools ##
------------------------------
Ubuntu 16.04 (Xenial Xerus) installed.  
Robot Operating System (ROS) Kinetic Kame distribution installed.  
Gazebo 7 Simulator used for testing.  



## How to deploy and run the package ## 
-------------------------------

### Path planning ###

1. Clone the repository: 
	```bash
	git clone https://github.com/gaowq1994/ee4308_uav uavWs
	```
	
2. Initialise the workspace: 
	```bash
	cd ~/uavWs/src
	catkin_init_workspace
	```
	
3. Compile the project: 
	```bash
	cd ~/uavWs
	sudo chmod 777 -R ./
	catkin_make
	```
  
4. Compile the C++ code for the A-star algorithm:
	```bash
	cd ~/uavWs/drone-path-planner
	g++ --std=c++11 -o Astar Astar.cpp
	```
5. Execute _Astar.exe_ to generate _coordinates.txt_ from _obstacles.txt_.
	```bash
	./Astar
	```

6. Use MATLAB to run _calc_all_continous.m_ from the drone-path-planner folder.

  This will generate _path.txt_ which will be used for navigation by the UAV.
  
### Simulation ###

7. Go to the uavWS workspace:
	```bash
	cd ~/uavWs
	```

8. Start simulation environment:
	```bash
	./setup
	```

9. Open the simulation script "sim" in the uavWs workspace.

10. Open a new terminal.

11. Substitute the address of the obstacles file and path file
	```bash
	rosrun hector_quadrotor_reference refPub _obsAdr:="/home/INSERT_YOUR_USERNAME/uavWs/drone-path-planner/obstacles.txt" _refAdr:="/home/INSERT_YOUR_USERNAME/uavWs/drone-path-planner/path.txt" 
	```
12. Run simulation:
	```bash
	./sim
	```

