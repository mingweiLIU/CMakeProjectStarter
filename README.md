<!--
 * @Descripttion: 
 * @version: 
 * @Author: 刘铭崴
 * @Date: 2019-11-23 22:44:18
 * @LastEditors: 刘铭崴
 * @LastEditTime: 2019-11-23 22:55:21
 -->
## 用于初始化创建CMake管理项目

## 设置vscode来采用conda环境变量
里面vscode的setting.json中设置了Anaconda的配置方法，拿到项目后请将自己的conda安装路径替换setting.json中的对应路径，以及需要激活的conda的环境变量。该设置的好处是：当vs code被启动时，会将控制台输入切换到conda prompt模式，且激活项目需要用到的环境变量（这里为atom），切换成功的表现是控制台输入路径前有（atom）的字样

## 安装conda环境变量
这里的atom.yml为个人的项目环境变量，可以通过在conda prompt中输入以下命令创建环境变量并安装相应的依赖库
```
conda env create -f atom.yml
```