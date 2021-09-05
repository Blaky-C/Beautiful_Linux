# About Install Linux

### 部分参考：

1. https://github.com/TonyCrane/Beautiful_Linux
2. 



### 安装说明



Optimize and beautify Ubuntu. 

### Optimize

参考：https://github.com/TonyCrane/Beautiful_Linux

1. 安装python：```sudo apt install python3```

2. 安装git并添加ssh密钥：

   ```shell
   sudo apt install git
   git config --global user.name "your_name"
   git config --global user.email "you@example.com"
   ssh-keygen -t rsa -C "your_email@youremail.com"  # 一路回车
   cat ~/.ssh/id_rsa.pub # 并复制粘贴到github上
   ssh -T git@github.com # 测试
   git clone https://github.com/Tony031218/Beautiful_Linux.git # 克隆下本仓库
   ```

3. 更换源 

   在 Software&Updates中设置即可

   ```shell
   sudo apt update
   sudo apt upgrade
   ```

4. 卸载 libreoffice 安装 WPS（可选）

   ``` sudo apt remove libreoffice-common ```

   从http://www.wps.cn/product/wpslinux/ 上下载 WPS：``` sudo dpkg -i wps-office_10.1.0.6757_amd64.deb ```








