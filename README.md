# 太阳系运行系统

## 原理
canvas和THREE接口实现三维视图的构建，通过建立不同的相机角度的视图，得到俯视图和侧视图，画中画的动画实现日食和月食的模拟。

## 运行配置
1.安装http-server,保存图片：
```shell
sudo npm install --global http-server
http-server --cors
```
2.更换图片路径为自己的路径，即代码中注释update your URL的位置的变量的值。
3.运行main3d.html文件即可
