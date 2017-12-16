# TeamBConvenienceScripts

These are scripts used by the BYU Senior Project in Fall 2017 for starting ROSplane nodes and setting relevant environment variables. Many of the scripts set the ROS_MASTER_URI to the IP we assigned to our plane, and this would need to be changed for use by others. We found that using these scripts was faster than directly running launch files when we were in the field on a flight, as they save a few steps of typing commands.

Here is a brief description of the purpose of the scripts:

<b>groundstation</b> - sets ROS IP, ROS master IP, runs ros_groundstation and starts recording a ros bag.

<b>load_params_cal.bash</b> - loads strato.yml, calibrates IMU, barometer, and airspeed sensor, and writes params

<b>rosodroid</b> - sets ROS_MASTER_URI to the odroid's IP (plane) and sets ROS_IP for the local machine. This should be sourced rather than run for the variables to persist in a terminal after the script exits.

<b>roslocal</b> - sets the ROS master to the local machine

<b>startbombdropgs</b> - runs everything needed for the bomb drop on the groundstation (bombdrop_gs.launch)

<b>startgs</b> - runs groundstation, bag, waypoint_planner, and rqt_reconfigure (tuning_gs.launch)

<b>startodroid</b> - starts everything needed for the bomb drop on the plane (estimator, autopilot, wind estimator, gps, rosflight_io, path manager/follower, bag - bombdrop.launch) There is also a bombdrop2.launch which just has the serial ports for GPS and airspeed swapped, because this seems to be random.

<b>startsim</b> - runs simulator with groundstation, waypoint planner, and rqt_reconfigure for tuning

<b>tune</b> - runs rqt_reconfigure

<b>waypointplanner</b> - runs the waypoint_planner node and a bag


A typical usage would be to run startodroid on the plane, followed by sourcing rosodroid on the groundstation, then running load_params_cal.bash and startgs or startbombdropgs.
