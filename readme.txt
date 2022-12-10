You can find additional info on this work in this thesis, however it's in italian:
https://mega.co.nz/#!bdYEWKDZ!WmsdbkD-DifIXAGAL4cHTBwb_hYw36mMpB_XMmLX5VA

You can also find in this repository the same Thesis translated to english (automatic google translation).

In order to run the simulation you will need: 
	ROS, Hector_quadrotor + hector_quadrotor_world, gazebo, Moveit! and the few extra in this .rar.

The external programs can be found here:
ROS               --->  http://wiki.ros.org/
Hector_quadrotor  --->  http://wiki.ros.org/hector_quadrotor
gazebo            --->  http://wiki.ros.org/gazebo
Moveit!           --->  http://moveit.ros.org/

First of all you should create a configuration pack for moveIt! in order to correctly interface it with hector quadrotor, in other word you should create a series of configuration file to correctly interface the quadrotor with the plugin.
You can do it by yourself following this tutorials ( http://moveit.ros.org/wiki/Quick_Start) and using my modified version of hector_quadrotor.urdf (you can find it in "hector_quadrotor/hector_quadrotor_urdf/urdf/quadrotore.urdf" ), just remember to add a virtual floating joint between the base link of the quadrotor and teh fixed odometry link... 
or you can simply use the pack I already made with everything configured --> quadrotore2_moveit.
In the second case everything should be configured correctly and the quadrotor should be able to build a map of the place and fly itself using moveit!. 
Now you just need to launch Gazebo and spawn the quadrotor("sh files/1-simulator.sh"), launch the action_controller node ("sh files/2-controllers.sh") and finaly launch the moveit plugin and rviz visualizer ("sh files/3-planner.sh"). Optionally you can spawn a node to teleoperate the quadrotor in the simulation from the terminal ("sh files/4-teleOp.sh").
Maybe in order to make the sh work you should change some path!

You can simply overwrite the standard's packages downloaded from the official wiki pages (like pr2_teleop, hector_quadrotor or moveit_simple_controller_manager) with my modified ones and recompile all in order to obtain the modified packages and the additional functionalities.
Contents of the folders:

->action_controller:
	 action controller to translate geometrical trajectory in cmd_vel to control the quadrotor, it automatically translate the geometrical 		traiectory produced by moveit in comand to make the quadrotor move.

->moveit_simple_controller_manager: 
	modified version of moveit_simple_controller_manager to handle multiDofFollowJointTrajectoryAction and to send the trajectory to the custom 		action_controller above defined

->hector_quadrotor:
	modified urdf of the quadrotor to publish the odometry of the joints

->pr2_teleop:
	simple node to teleop the simulated quadrotor using the keyboard

->quadrotore2_moveit:
	configuration file for moveit!

->sh files:
	bash file to launch the different part of the simulation
