userdel

相关命令：deluser
userdel-删除使用者帐号及相关档案

语法
userdel[-r]login

描述

userdel命令修改系统帐号档删除所有login会参考的部份。使用者名称必须是存在的。

-r
使用者目录下的档案一并移除。在其他位置上的档案也将一一找出并删除。


档案

/etc/passwd-使用者帐号资料

/etc/shadow-使用者帐号资讯加密

/etc/group-群组资讯

警告

userdel不允许你移除正在线上的使用者帐号。你必须砍掉此帐号现在在系统上执行的程序才能进行帐号删除。不能在NISclient端移除NIS属性的东西。这动做须在NISserver端上执行。
