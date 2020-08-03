## Unity 2D 游戏开发 入门级引导

### 引言

本文档主要根据个人学习计划的学习和实践过程中的2d游戏开发经验总结得出， 适合刚准备上手Unity开发实践前阅读，可以对Unity的开发有一个初步的了解。

在这里十分推荐一个Unity的官方出的2D开发教程—— [Ruby's Adventrue: 2D Beginner](https://learn.unity.com/project/ruby-s-2d-rpg?uv=2019.2)。 如果你能一步一步跟随教程走下来 相信你就能掌握Unity以及Unity的2D开发的基础了, 后面就可以自己着手进行开发 细节相关的API还有一些Class可以通过查阅官方文档和Unity的论坛来解决。推荐两个youtebe频道 [Brackeys](https://www.youtube.com/channel/UCYbK_tjZ2OrIZFBvU6CCMiA) 和 [Code Monkey](https://www.youtube.com/c/CodeMonkeyUnity) , 里面有很多unity开发相关的视频, 可以平常挑感兴趣的部分学习学习， 解决问题的话 还是google一下靠谱。

### 准备工作

#### Unity安装

1. 在Unity官网注册一个新的个人账号。这点十分重要， 想要启动Unity就需要个人账号激活免费证书 一般一周左右就需要更新一次。
2. 在Unity官网 下载最新的 UnityHub , 新版的Unity都是通过Unity Hub 作为启动器来启动的。
3. 在Unity Hub的 设置 => 许可证管理 里激活新的个人许可证
4. 在Unity Hub 安装 选项里选择下砸的unity版本 目前的时间点 2020年8月， 不太推荐下载2020的beta版本 还不是所有的功能都支持。推荐下载2019.4左右的稳定版本。
5. 在漫长的下载之后 在项目 下新建一个2D Unity的项目 并打开。至此就可以正式开始Unity的开发之旅了。

#### 相关知识学习

1. C#的基础语法。 如果你有面向对象的强类型语言开发 如Java 那么C#上手不会非常困难。
2. 基本的立体几何和平面几何的知识。 (主要涉及 坐标 变换 摄像机等)
3. Shader相关的 编程知识。 (GPU渲染相关 做渲染需要掌握)
4.  贴图相关知识。(不同贴图的类型 作用 使用场景 3D使用的比较多)

### 界面

由于Unity的界面繁多 我主要挑几个最重要最常用的讲，基本所有的开发用到的界面都能在顶部的窗口(Window)那个下拉菜单里找到。特别提一下布局(Layouts)， 这是Unity默认配置的窗口布局，个人比较推荐 2by3，不过不同游戏可能有不同的需求。

1. 场景(Scene)

   这个界面是你开发过程中国主要的可视化的互动界面，你可以在



![image-20200803174520037](/Users/yangyifan/Library/Application Support/typora-user-images/image-20200803174520037.png)