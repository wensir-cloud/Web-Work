<!-- 对实现思路、使用说明、遇到问题及解决办法进行准确的描述，并且列出所有参考资料。 -->

# 太阳系运行系统 说明文档

文雨 郑若琪 付家华

## 实现思路

我们使用[Three.js](https://threejs.org/)库模拟了一个3D太阳系的场景。

画面中呈现了太阳系的3D视图、侧视图和顶视图，还有画中画形式的日食和月食天象，包括全食、环食和偏食。

我们准备了两套图片资源用于切换展示，还包含一个带有ID“change”的按钮，用于在两种不同的地球纹理之间切换。

script部分是代码的核心部分。下面简单阐述工作流程：

首先，设置变量，并加载太阳、地球和月球的图像纹理。创建了三个不同的相机，用于3D视图、侧视图和顶视图。创建了三个不同的渲染器，用于渲染各自的视图。使用Three.js的几何体、材质和网格设置了太阳、地球和月球的3D对象。定义了地球和月球的公转轨道，使用了Object3D和LineLoop。处理了按钮点击事件，用于在两种地球纹理之间切换。包含一个名为animate()的函数，负责更新太阳、地球和月球在2D画布中的位置和3D场景中的位置。这个函数还旋转3D对象以创建动画效果。使用requestAnimationFrame()递归地调用animate()函数，以创建平滑的动画循环。

关于资源的访问，代码期望多个图像资源，包括：

- "/sun.png"：太阳的纹理。
- "/earth.png"和"/new_earth2.png"：两种地球的纹理（可由"change"按钮切换）。
- "/moon2.png"：月球的纹理。
- "/moon_2d.png"和"/sun_2d.png"：月球和太阳的2D图像，分别渲染在2D画布中。

方便起见将图片放在了html文件的同级目录下。启动html前需要在项目的根目录启动http-server，来通过8080端口提供这些图片。

## 使用说明

首先进入项目根目录，运行`http-server`。

```shell
npm install --global http-server
http-server --cors
```

`http-server`默认运行在`127.0.0.1:8080`上，如果环境不同，可以自行修改html的代码中`httpServerBaseUrl`的定义。

然后运行`main3d.html`即可看到效果。

## 问题与解决

1. 为了方便为地球换肤，我们通过url而不是相对路径的方式访问图片。但是这样会涉及到跨域访问的问题，需要在`http-server`的启动选项中加上`--cors`。
2. 相机高度相同时，发现有时俯视图显示不全，通过提高俯视图相机的高度解决。

## 参考资料

1. [Three.js](https://threejs.org/)
2. [http-server](https://www.npmjs.com/package/http-server)
3. [[Question] How to set cors headers? - Github Issues](https://github.com/http-party/http-server/issues/308)
