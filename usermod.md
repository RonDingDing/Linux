## usermod

相关命令：暂无相关命令

名称

usermod-修改使用者帐号

语法

    usermod [-ccomment] [-dhome_dir[-m]] [-eexpire_date] [-finactive_time] [-ginitial_group] [-Ggroup[,...]] [-llogin_name] [-sshell] [-uuid[-o]] login

描述

usermod命令会参照你命令列上指定的部份修改系统帐号档。下列为usermod可选用的参数。

|选项|描述|
|:-------------:|:-----:|
|-a append|把用户追加到某些组中，仅与-G选项一起使用
|-c comment|更新使用者帐号password档中的注解栏，一般是使用chfn(1)来修改。|
|-d home_dir|更新使用者新的登入目录。如果给定-m选项，使用者旧目录会搬到新的目录去，如旧目录不存在则建个新的。|
|-e expire_date|加上使用者帐号停止日期。日期格式为MM/DD/YY。|
|-f inactive_days|帐号过期几日后永久停权。当值为0时帐号则立刻被停权。而当值为-1时则关闭此功能。预设值为-1。|
|-g initial_group|更新使用者新的起始登入群组。群组名须已存在。群组ID必须参照既有的的群组。群组ID预设值为1。|
|-G group,[...]|定义使用者为一堆groups的成员。每个群组使用","区格开来，不可以夹杂空白字元。群组名同-g选项的限制。如果使用者现在的群组不再此列，则将使用者由该群组中移除。|
|-l login_name|变更使用者login时的名称为login_name。其于不变。特别是，使用者目录名应该也会跟着更动成新的登入名。|
|-s shell|指定新登入shell。如此栏留白，系统将选用系统预设shell。|
|-L |锁定一个用户的帐号。这个操作是放一个感叹号在你的密码前，禁用密码。你不能配合-p或-U使用。|
|-U |解锁一个用户的帐号。这个操作是在加密密码前取消感叹号，恢复帐号登录。你不能配合-p或-L使用。|
|-u uid|使用者ID值。必须为唯一的ID值，除非用-o选项。数字不可为负值。预设为最小不得小于999而逐次增加。0~999传统上是保留给系统帐号使用。使用者目录树下所有的档案目录其userID会自动改变。放在使用者目录外的档案则要自行手动更动。||
警告

usermod不允许你改变正在线上的使用者帐号名称。当usermod用来改变userID，必须确认这名user没在电脑上执行任何程序。你需手动更改使用者的crontab档。也需手动更改使用者的at工作档。采用NISserver须在server上更动相关的NIS设定。

档案

/etc/passwd-使用者帐号资讯

/etc/shadow-使用者帐号资讯加密

/etc/group-群组资讯

相关文件
chfn(1),chsh(1),groupadd(8),groupdel(8),groupmod(8),passwd(1),useradd(8),userdel(8)
