# Ros环境部署

#### 介绍
ros环境快速部署，使用广西省第四届大学生人工智能设计大赛--无人驾驶竞速赛项相关资料进行参照部署测试

#### 软件架构
该工作空间的运行需要保证ros以及相关功能包的安装
该项目可以在ubuntu18.04-melodic以及ubuntu20.04-noetic正常使用，其他版本未作测试

### 环境部署说明
可直接运行sudo sh install_Ros.sh进行环境快速部署
若出现错误有两个解决方案：
1、缺少相关的功能包，需要另外添加
2、先运行source ./devel/setup.bash后再运行ros环境


#### 使用前说明

1. 建议安装双系统而非虚拟机模式运行，双系统安装可以参考“Ubuntu双系统.pdf”
2. 安装指定版本的ROS，可以终端命令一键安装'wget http://fishros.com/install -O fishros && sudo bash fishros'
3. 安装gmapping'sudo apt-get install ros-{ros版本号}-gmapping'
4. 安装move_base'sudo apt-get install ros-{ros版本号}-move-base'
5. 如果还缺少其他功能包，按照类似上面的方式进行安装
6. 使用终端命令'cd && git clone xxx'克隆代码
7. 编译工作空间'cd ~/u1car_ws/ && catkin_make'
8. 打开~/.bashrc文件并添加'source ~/u1car_ws/devel/setup.bash'添加环境变量
9. 将src文件夹里的end_plane和construction_cone文件夹放入~/.gazebo/models/目录下（使用'ctrl+h'可以查看隐藏文件），不然在联网情况下gazebo很难打开。如果没有这么操作，gazebo会报错，出现无法现实锥桶或者终点地标的情况

#### 使用说明
工作空间已包含基础功能包，需要参赛队伍在基础工作空间下各部分的功能优化
1.  启动仿真环境
终端命令输入'roslaunch u1car_gazebo Run_world.launch'即可启动gazebo仿真环境
正常情况下，启动之后环境之中包括了赛道、小车、终点标识
2.  实现基本控制
终端命令输入'rosrun teleop_twist_keyboard teleop_twist_keyboard.py'
按照提示即可完成基本的控制
3. 启动建图
启动环境之后，终端命令输入'roslaunch u1car_map Run_map.launch'
使用基本控制完成建图即可
完成建图后需要使用以下两个命令保存地图：
'cd ~/u1car_ws/src/u1car_nav/map/'
'rosrun map_server map_saver'
4. 启动自主导航
启动环境之后，终端命令输入'roslaunch u1car_nav Run_nav.launch'
点击rviz可视化界面中的'2D Nav Goal'，并在地图中发布终点即可开始导航

#### 视频录制说明
1. 录制工具可以采用kazam
ubuntu下可以直接使用'sudo apt-get install kazam'进行安装，终端中使用命令'kazam'命令即可打开软件
2. 视频要求
视频内容要求能够全面看清楚gazebo仿真环境和rviz可视化环境
要求视频应展示小车运行全过程，且运行过程中完全自主，不得进行人为干预

#### 导航优化建议
1. 优化自带的参数
2. 下载并参考功能包"teb_local_planner_tutorials"中的参数（推荐）


