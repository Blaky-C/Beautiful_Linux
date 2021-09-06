# Initialize and Optimize Linux

#### Initialize:

参考：https://github.com/TonyCrane/Beautiful_Linux

1. 通过 ```nomodeset``` 命令进入系统之后，在 **软件更新** 中先替换 Ubuntu 的软件源，然后选择一个合适的显卡驱动，重启调整分辨率。

   * 

2. 安装 git，添加 ssh 密钥，并生成token：

   * ```shell
     sudo apt install git
     git config --global user.name "your_name"
     git config --global user.email "you@example.com"
     ssh-keygen -t rsa -C "your_email@youremail.com"  # 一路回车
     cat ~/.ssh/id_rsa.pub # 并复制粘贴到github上
     ssh -T git@github.com # 测试
     git clone https://github.com/Tony031218/Beautiful_Linux.git # 克隆下本仓库
     ```

   * 关于 github 弃用账号密码登陆的 token 认证方式：

3. 安装 Chrome、Typora 和 坚果云：

   * Chrome 安装包在 ```packages``` 文件夹下，Typora 直接在官网安装即可
   * 坚果云安装后打不开：**待解决**
   * 尝试用 iCloud 代替：

4. 简介





### Optimize

##### 设置 SSH 服务和远程访问工具

参考：https://mculover666.blog.csdn.net/article/details/84613627

文章从基于 SSH 的远程访问、远程文件传输，再到 VNC 的远程桌面控制，讲的非常详细，但是自己在配置远程桌面时，不想额外安装 gnome2 桌面服务，另外参考了：https://www.cnblogs.com/xuliangxing/p/7642650.html，额外安装了 xrdp、xbase-clients，以及 dconf-editor 用去取消加密权限限制。

此外，使用 VNC 远程访问的延迟有点让人难以接受，参考：https://www.cnblogs.com/bandiao/p/10778508.html 进行了细微调整，但还有明显的延滞感。

win10 无法 ping 通 Ubuntu 的问题：https://blog.csdn.net/hyy_217/article/details/72779642



##### 无法通过键鼠控制系统

参考：https://blog.csdn.net/weixin_45368686/article/details/105585732 

中途突然出现了无法通过键鼠控制系统的情况，安装相应的键鼠驱动解决。



##### 创建系统镜像



