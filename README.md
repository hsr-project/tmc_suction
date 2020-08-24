概要
=============================
* 吸引機能を利用するためのアクションを提供する。
* 吸引開始/終了を行うことができる。
* 吸引開始を行う場合、タイムアウト時間内に実際に物を吸引できたかどうかが結果として返ってくる。

開発関係者
================
* 村瀬和都

クラス
================

SuctionServer
-------------
* 吸引機能のためのアクションサーバークラス

インターフェース
================
### 提供するアクション ###
tmc_suction/SuctionControlActionGoal : "/suction_control/goal":
- duration timeout : 物体吸引タイムアウト時間(タイムアウトしたら吸引終了する)
- std_msgs/Bool suction_on: True:吸引開始 False:吸引終了

tmc_suction/SuctionControlActionResult : "/suction_control/result":
- actionlib_msgs/GoalStatus status : - actionlib_msgs::GoalStatus::PREEMPTED アクション中断   - actionlib_msgs::GoalStatus::SUCCEEDED 正常終了 - actionlib_msgs::GoalStatus::ABORTED 異常終了(物体吸引タイムアウト) - actionlib_msgs::GoalStatus::REJECTED ゴール棄却(タイムアウト時間durationに負値が入っていた場合)

### 購読するトピック ###
std_msgs/Bool : "/pressure_sensor_on": 実際に物を吸引しているかどうかデバイス側から取得

### 発行するトピック ###
std_msgs/Bool : "/suction_on": デバイス側に吸引開始/終了の命令を伝える

LICENSE
================
* This software is released under the BSD 3-Clause Clear License, see LICENSE.txt.
