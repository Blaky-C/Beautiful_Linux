# About Install Linux

### 目录

1. InitializaAndOptimize：初始化配置和优化 Ubuntu 系统
2. Beautify：美化 Ubuntu 工具
3. VMware_Ubuntu：在虚拟机中安装 Ubuntu 的方法
4. 



### 安装说明

这里直接记录安装 Ubuntu 过程中遇到的一系列坑。



##### 库和镜像

Ubuntu 的各版本网易镜像：http://mirrors.163.com/ubuntu-releases/

Ubuntu 的软件包/依赖库查询：https://www.debian.org/distrib/packages#search_contents



##### U盘安装双系统方式

详细的安装过程参考：https://www.cnblogs.com/masbay/p/10844857.html

注意：

1. 在 Ubuntu 系统中分盘时，efi 分区必须和 Window 的启动分区在同一磁盘上。这次在装Ubuntu18.04 的时候，把 efi 分区单独装在了机械硬盘上，结果出现了安装完 Ubuntu 启动时在 BIOS 内找不到引导的情况。（该情况用 boot-repair 工具也没有成功修复：参考：https://www.cnblogs.com/lymboy/p/7783756.html 和 https://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow）



##### 进入系统时黑屏问题

显卡驱动存在问题，通过进入recovery模式修改grub登陆系统

```shell
# 选择 recover mode 进入后
# 选择 root Drop to root shell prompt

# 以读写权限挂载系统分区
mount -o remount /

# 修改 grub 启动文件
vi /etc/default/grub
# 将文件中的GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  修改为GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
# 输入:wq 保存退出

# 更新配置
update-grub

# 按 Ctrl+D 后选择 resume 重新进入系统即可
```

参考：https://blog.csdn.net/a845717607/article/details/98449419

但是依然存在分辨率问题待修复（见下一条修复）



##### 分辨率修复

进入系统之后，屏幕的分辨率一直都是1024*768，反复换了好几次显卡驱动，重启之后都未果。也尝试了直接更改显示分辨率的配置文件，在这个过程中发现通过 ```nvidia-settings``` 命令打开显卡设置界面时只打开了一个空白面板，发现显卡驱动安装一直没有成功，原因是BIOS面板中的Security Boot没有设为【禁用】。

解决方案参考：

1. 删除和修改显卡驱动尽量选择系统自带的可视化操作，在 **软件和更新** 的 **附加驱动** 中
2. 命令行删除并重装显卡驱动：https://zhuanlan.zhihu.com/p/258807165
3. 华硕主板关闭 Secure Boot 和 Fast Boot：http://www.winwin7.com/JC/12235.html
4. 显卡驱动安装的重启验证：https://blog.csdn.net/u011573853/article/details/112312350



##### 网卡驱动安装（不一定需要）

因为给主机装了额外的内置网卡，本来以为可能需要再装网卡驱动，但是买的 AX200 装上之后在 Ubuntu 上直接就可以用。

参考：https://blog.csdn.net/haigujiujian/article/details/114914875













