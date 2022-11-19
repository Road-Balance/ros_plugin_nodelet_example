# ROS Plugin and Nodelet Example

Examples for ROS Plugin and Nodelet

* plugin run

```bash
# Querying the list of plugins in a package
$ rospack plugins --attrib=plugin pluginlib_calculator

# Running the plugin loader
$ roscore
$ rosrun pluginlib_calculator calculator_loader
```

* nodelet run

```bash
$ roscore
$ rosrun nodelet nodelet manager __name:=nodelet_manager
$ rosrun nodelet nodelet load nodelet_hello_world/Hello nodelet_manager __name:=nodelet1

$ rostopic list
/nodelet1/msg_in
/nodelet1/msg_out
/nodelet_manager/bond
/rosout
/rosout_agg

$ rostopic pub /nodelet1/msg_in std_msgs/String "Hello"
$ rostopic echo /nodelet1/msg_out
```

* nodelet launch

```
# Terminal 1
$ roslaunch nodelet_hello_world hello_world.launch

# Terminal 2
$ rostopic echo /test1/msg_out

# Terminal 3
$ rostopic pub /test1/msg_in std_msgs/String "Hello"
```