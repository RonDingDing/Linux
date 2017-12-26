useradd - 帐号建立或更新新使用者的资讯

     useradd [-c comment] [-d home_dir]
         [-e expire_date] [-f inactive_time]
         [-g initial_group] [-G group[,...]]
         [-m [-k skeleton_dir] | -M] [-s shell]
         [-u uid [ -o]] [-n] [-r] login

  

     useradd -D [-g default_group] [-b default_home]
         [-f default_inactive] [-e default_expire_date]
         [-s default_shell]

新帐号建立：

当不加-D参数,useradd指令使用命令列定新帐号的设定值and使用系统上的预设值.新使用者帐号将产生一些系统档案，使用者目录建立，拷备起始档案等，这些均可以利用命令列选项指定。此版本为RedHatLinux提供，可帮每个新加入的使用者建立个别的group,毋须添加-n选项。useradd可使用的选项为

|选项|描述|
| ------------- |:-------------:|
|-c comment|新帐号password档的说明栏。|
|-d home_dir|新帐号每次登入时所使用的home_dir。预设值为default_home内login名称，并当成登入时目录名称。|
|-e expire_date|帐号终止日期。日期的指定格式为MM/DD/YY。|
|-f inactive_days|帐号过期几日后永久停权。当值为0时帐号则立刻被停权。而当值为-1时则关闭此功能，预设值为-1|
|-g initial_group|group名称或以数字来做为使用者登入起始群组(group)。群组名须为现有存在的名称。群组数字也须为现有存在的群组。预设的群组数字为1。|
|-G group,[...]|定义此使用者为此一堆groups的成员。每个群组使用","区格开来，不可以夹杂空白字元。群组名同-g选项的限制。定义值为使用者的起始群组。|
|-m|使用者目录如不存在则自动建立。如使用-k选项skeleton_dir内的档案将复制至使用者目录下。然而在/etc/skel目录下的档案也会复制过去取代。任何在skeleton_diror/etc/skel的目录也相同会在使用者目录下一一建立。|
|-k|同-m，不建立目录以及不复制任何档案为预设值。|
|-M|不建立使用者目录，即使/etc/login.defs系统档设定要建立使用者目录。|
|-n|预设值使用者群组与使用者名称会相同。此选项将取消此预设值。|
| -r|此参数是用来建立系统帐号。系统帐号的UID会比定义在系统档上/etc/login.defs.的UID_MIN来的小。注意useradd此用法所建立的帐号不会建立使用者目录，也不会在乎纪录在/etc/login.defs.的定义值。如果你想要有使用者目录须额外指定-m参数来建立系统帐号。这是REDHAT额外增设的选项。|
|-s shell|使用者登入后使用的shell名称。预设为不填写，这样系统会帮你指定预设的登入shell。|
|-u uid|使用者的ID值。必须为唯一的ID值，除非用-o选项。数字不可为负值。预设为最小不得小于999而逐次增加。0~999传统上是保留给系统帐号使用。|

改变预设值

当-D选项出现时，useradd秀出现在的预设值，或是藉由命令列的方式更新预设值。可用选项为∶

|选项|描述|
| ------------- |:-------------:|
|-b default_home|定义使用者所属目录的前一个目录。使用者名称会附加在default_home后面用来建立新使用者的目录。当然使用-d后则此选项无效。|
|-e default_expire_date|使用者帐号停止日期。|
|-f default_inactive|帐号过期几日后停权。|
|-g default_group|新帐号起始群组名或ID。群组名须为现有存在的名称。群组ID也须为现有存在的群组。|
|-s default_shell|使用者登入后使用的shell名称。往后新加入的帐号都将使用此shell。|

如不指定任何参数，useradd显示目前预设的值。

注记

系统管理者有义务在/etc/skel目录下放置使用者定义档。
此版本『useradd』由RedHat修改。

警告

不可新增使用者于NIS群组中。你必须在NIS伺服器上执行。

档案

/etc/passwd-使用者帐号资讯

/etc/shadow-使用者帐号资讯加密

/etc/group-群组资讯

/etc/default/useradd-定义资讯

/etc/login.defs-系统广义设定

/etc/skel-内含定义档的目录
