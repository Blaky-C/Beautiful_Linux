# Affr 安装

Github: https://github.com/dpa1mer/arff



### Matlab

1. 下载 matlab r2020b：http://itc.zju.edu.cn/matlab/list.htm

2. 注意：安装的过程中以 root 用户权限进行安装

3. 添加软链接支持命令行打开：

   ```shell
   sudo ln -s /usr/local/MATLAB/R2020b/bin/matlab /usr/local/bin/matlab
   ```

4. 通过 ``` sudo su ``` 打开 matlab 之后在附加功能里添加 ```MatPlotLib Colormaps``` 工具包





### Manopt

1. 下载安装包：https://www.manopt.org/，直接解压后放在 ```/usr/local/Toolkits/``` 下（安装 5.0 版本）

2. 在 matlab 中保存 manopt 的路径，测试运行，成功即可

   ```shell
   # 保存路径
   importmanopt
   
   # 测试安装情况
   cd checkinstall/
   basicexample()
   ```

   



### Mosek 

1. 下载：https://www.mosek.com/downloads/list/9/

   安装指南：https://docs.mosek.com/9.0/install/installation.html

2. 将 Mosek 添加到环境变量 Path：

   ```shell
   # 对所有用户添加环境变量
   sudo vim /etc/profile
   
   # 在最后添加
   export PATH=$PATH:/usr/local/Toolkits/mosek/9.0/tools/platform/linux64x86/bin
   
   # 更新环境变量
   source /etc/profile
   ```

   Ubuntu 添加环境变量的方法：https://blog.csdn.net/White_Idiot/article/details/78253004

3. 申请 Personal Academic License：https://www.mosek.com/products/academic-licenses/

   下载之后将 mosek.lic 文件复制到 ```$HOME/mosek/mosek.lic``` 下

   如果 matlab 以 root 用户安装，需要复制到 ```/root/mosek/mosek.lic``` 下

   

4. 构建 fusion

   ```shell
   cd <MSKHOME>/mosek/9.0/tools/examples/fusion/cxx
   sudo make all
   ```



### tbb

1. Ubuntu 直接通过 APT 安装：``` sudo apt install libtbb-dev ```

2. 在 CMakeLists.txt 中链接动态库：

   ```cmake
   target_link_libraries(00_helloworld /usr/lib/x86_64-linux-gnu/libtbb.so)
   ```



### Eigen

直接在 APT 中安装即可：```sudo apt install libeigen3-dev ```



### 安装 ARFF

1. 下载项目：https://github.com/dpa1mer/arff

2. 配置前保证 Matlab 和 gcc 对应的 stdlibc++.so.6 库版本一致：

   ```shell
   # 查找 Matlab
   find /usr/local/ -name libstdc++.so.6*
   
   # 查找 gcc
   find /usr/lib/ -name libstdc++.so.6*
   ```

   自己用的版本都是 ```libstdc++.so.6.0.25```

3. 安装

   在 matlab 命令行内打开至 arrf 项目根目录，将所有的文件通过 mex 编译至对应位置：

   ```shell
   cd src/batchop
   mexbuild /path/to/tbb/include
   cd ../sdp
   mexbuild /path/to/tbb/include /path/to/mosek/9.0
   cd ../../ext/ray
   mexbuild /path/to/eigen3 /path/to/tbb/include
   cd ../..
   install
   ```

   注意：过程中会要求安装相应的 Matlab 工具箱，需要通过命令 ``` sudo apt install nvidia-cuda-dev ``` 安装 Cuda

4. 将 ```sdp/variety/``` 添加至路径

5. 执行

   ```matlab
   mesh = ImportMesh('meshes/rockerarm_91k.mesh');
   qOcta = MBO(mesh, OctaMBO, [], 50, 3);
   VisualizeResult(mesh, qOcta);
   ```











