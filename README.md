# Beautiful_Linux
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



### Beautify

##### 壁纸文件

参考：https://github.com/TonyCrane/Beautiful_Linux

采用了壁纸：![Forever_by_Shady_S.jpg](./Forever_by_Shady_S.jpg)



##### Theme和Icon文件下载

主题本来想使用之前用的 unity-tweak-tool 加 Flatabulous 的，但是在 Ubuntu 20.4中安装时，启动unity-tweak-tool和安装 Flatabulous 库均出现了问题，因此改用 gnome-tweak-tool。

参考：https://zhuanlan.zhihu.com/p/340468652

1. 下载文件后将Theme和Icon相关文件分别放入```/home/<username>/``` 下的 ```.themes/``` 和 ```.icons/``` 文件下即可
2. 通过 ``` Alt+F2``` 后输入 ```r``` 可以刷新tweak的界面显示
3. Orchis gtk主题地址：https://www.opendesktop.org/s/Gnome/p/1357889/
4. Tela icon地址：https://www.opendesktop.org/s/Gnome/p/1357889/



##### Dock相关优化

参考：https://zhuanlan.zhihu.com/p/176977192

1. 在命令行里安装 ```gnome-tweaks``` 和 ```chrome-gnome-shell```
2. 在 https://extensions.gnome.org 上分别安装Chrome的gnome插件、user themes、dash to dock和netspeed
3. 在dash to dock的配置界面 https://extensions.gnome.org/local/ 对dash进行配置



