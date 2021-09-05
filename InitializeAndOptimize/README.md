# Initialize and Optimize Linux

#### Initialize:

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
   * 坚果云安装后打不开：

4. 简介

