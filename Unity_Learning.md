## Unity 2D 游戏开发 入门级指南

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

#### 相关知识储备

1. C#的基础语法。 如果你有面向对象的强类型语言开发 如Java 那么C#上手不会非常困难。
2. 基本的立体几何和平面几何的知识。 (主要涉及 坐标 变换 摄像机等)
3. Shader相关的 编程知识。 (GPU渲染相关 做渲染需要掌握)
4.  贴图相关知识。(不同贴图的类型 作用 使用场景 3D使用的比较多)

### 界面

由于Unity的界面繁多 我主要挑几个最重要最常用的讲，基本所有的开发用到的界面都能在顶部的窗口(Window)那个下拉菜单里找到。特别提一下布局(Layouts)， 这是Unity默认配置的窗口布局，个人比较推荐 2by3，不过不同游戏可能有不同的需求。

这里稍微解释一下一些专有名词方便后面理解：

**游戏对象(GameObject)**:  场景里的一个最小容器, 用来承载不同组件 包含生命周期的最小元件。

**预设(Prefab)**:  可以理解为GameObject的模版，用于批量生成相似的GameObject。

**刚体(Rigidbody)**:  可以为游戏对象赋予物理属性，使游戏对象在物理系统的控制下接受推力与扭力，从而实现现实世界中的运动效果。

**碰撞盒(Collider)**: 字面上的意思, Unity系统用来检测碰撞的组件。

**平铺砖块(Tile)**: 2d游戏开发常用的一种块状的贴图用来做背景以及游戏物体的绘制。通常会把许多的这样的小块放在一张图里然后读取出来进行绘制。



##### 基础界面

1. **场景(Scene)**

   这个界面是你开发过程中国主要的可视化的互动界面，你可以在这个界面使用上方工具栏的工具和你的游戏对象(GameObject) 进行互动 比如 移动位置 旋转 拖动场景视窗等。在场景里除了UI部分的窗口和位置和实际显示的有差异， 大部分都是即见即所得， 你可以在场景里看到动画和粒子效果的演示。 值得一提的是当你点击预览播放按钮的时候, 你的场景预览视窗是不会跟随镜头的移动而改变的。
   
   
   
   <center><img alt='场景(Scene)' src='https://pic3.zhimg.com/80/v2-97acf833686728bb08aefb7198aa1dbe_720w.png' height=300px/></center>
   
    <center>场景(Scene)窗口</center>

2. **游戏(Game)**

   这个界面相对而言就比较直观了 就是你通过镜头播放并加上UI合成最后得到的输出画面的预览, 可以选择不同的摄像机来获得不同的视角，gizmos tab下的选项可以显示或关闭视图内的图标等标识。

​		

<center><img src='https://pic4.zhimg.com/80/v2-178df22745339dfcf23d4ce8643c462b_720w.png' alt='游戏(Game)' height=300px /></center>

<center>游戏(Game)窗口</center>

3. **层级(Hierarchy)**

   显示某个 场景(Scene) 的所有GameObject 以及它们之间的层级关系。在层级里你可以很方便的拖动来控制层级关系 也可以很方便的通过拖动实例化（预设）Prefab 以及创建某些GameObject 如 图像精灵(Image Sprite)。

<center><img src='https://pic1.zhimg.com/80/v2-f187f991d3672a3d4702b550516061e0_720w.png' alt='游戏(Game)' height=300px /></center>

<center>层级(Hierarchy)窗口</center>

4. **检查器(Inspector)**

   用于展示GameObject或其他对象的属性，大部分细节上的控制都是在这里发生的: 调节相关的参数， 添加对应的组件。粒子效果(Particle System)就有相当多的参数tab在检查器里配置调参。这里有一个非常实用的功能，就是很多参数都可以通过拖动的形式来赋值，以后会经常用到。

<center><img src='https://pic4.zhimg.com/80/v2-9a1c34a1f9a605032954cc89d5cec4bc_720w.png' alt='游戏(Game)' height=400px /></center>

<center>检查器(Inspector)窗口</center>

5. **项目(project)**

   这里存储了所有的项目文件 在Unity的目录下的，值得一提的是只有在Unity里创建或导入的资源包 才会真正被录入， 因为Unity会同时生成一个meta文件来记录详细信息。特别是C#脚本 如果通过IDE或者编辑器来创建的话是没法在Unity里互动的。

<center><img src='https://picb.zhimg.com/80/v2-659e05abd263b8149e4e1a7298fffadd_720w.png' alt='游戏(Game)' height=400px /></center>

<center>项目(Project)窗口</center>

6. **项目设置(project setting)**

   在 Edit => Project Setting里

   这个设置界面也是非常关键的， 里面涉及到了层级之间的碰撞关系，还有图像的渲染顺序等 全局的相关基本设置。 需要去了解一下主要用到的一部分 比如 Input Manager （控制标准输入的), Physics 2D (控制2d的物理沙盒属性) 。

<center><img src='https://pic2.zhimg.com/80/v2-c54e986ecd7e8f6c9916d92721b6cf42_720w.png' alt='游戏(Game)' height=300px /></center>

<center>项目设置(project setting) 界面</center>

7. **控制台(Console)**

   熟悉的老朋友，跟大部分IDE的控制台差不多，掌控着Unity的C#脚本里的输出以及错误处理，是你可以信赖的调试神器。遇事不决 Debug.Log()
   
   <center><img src='https://pic2.zhimg.com/80/v2-eaec34762589c905c81a7fa243f1425a_720w.png' alt='游戏(Game)' height=300px /></center>

<center>控制台(Console)界面</center>

##### 其他界面

8. **动画（Animations)**

   主要是用于动画片段的制作以及调试，不过你需要先选中一个GameObject对象之后才能进行动画的编辑, 在你导入了相关的Sprite之后, 还可以对他们进行一些变换操作。

   <center><img src='https://pic1.zhimg.com/80/v2-1c235f67cebcfbeb018eef97b26b73a5_720w.png' alt='游戏(Game)' height=300px /></center>

   <center>动画(Animation)界面</center>

9. **动画器（Animator)**

   对动画之间的切换过渡进行处理， 主要内容是动画的状态机， 在不同的状态下去播放不同的动画。通过脚本设置动画器的相关参数来驱动动画器里的动画状态机。

   <center><img src='https://pic1.zhimg.com/80/v2-736179c2f036ad7e998087529bde2d2d_720w.png' alt='游戏(Game)' height=300px /></center>

   <center>动画器(Animator)界面</center>

10. **画板(Palette)**

    平铺转经常用的用来绘制平铺地图(Tile Map)的工具，通过导入生成的单独的平铺砖 来对grid里的平铺地图进行填充。(Tips: 可以用shift + [ 或 ] 来翻转砖块。)
    
    <center><img src='https://pic4.zhimg.com/80/v2-7e086f5a147a1eeb07444c3b6e4ad1c9_720w.png' alt='游戏(Game)' height=300px /></center>
    
    <center>画板(Palette)界面</center>





### 常见场景

在这里我还是强烈推荐，如果想从0开始做一个2d的游戏 那么我非常建议跟着ruby's adventure的教程一课一课走下去，学完之后就能靠那些基础做一个像样的2d游戏架子了。 下面我会举一些常见的场景来讲解一些功能的实现:

1. **如何创建一个带图的游戏对象？**

     首先你需要的是把所有的资源导入到Unity的Assets里, 拿一个png为例，你点右边的小箭头会出现一个气泡 里面也是原图。 这个气泡里的东西本身就是sprite对象， 直接拖到scene里面就可以直接生成一个sprite的GameObject了，在右边的inspector里的sprite renderer 组件里能看到这个引用。如果原图的sprite发生了改变，那么绑定了这个sprite的gameobject也会改变。  

      

2. **如何让游戏对象移动？**

   首先让游戏对象移动基本上都是要使用脚本的，你需要做的就是在unity 创建一个C#脚本, 让后将脚本拖到你想要控制的对象上。

   基本上来说有两种模式:

    一种是设置物体的速度 让物理系统去处理位置变化, 不过需要给对象加上Rigidbody2D组件。形如：

   ```c#
   Rigidbody2D rigidbody2d = GetComponent<Rigidbody2D>();
   Vector2 SpeedNow = rigidbody2d.velocity;
   SpeedNow.x = 8.0f;
   rigidbody2d.velocity = SpeedNow;
   ```

   

      还有一种是自己计算变化，直接在Update的生命周期里设置坐标来实现位移。 

   ​	计算坐标的时候也有两种计算变化的方式一个是根据每帧的刷新去设置变化值，还有一种是利用Unity自带的Time类里的deltaTime来计算变化值。

   

3. **如何创建并控制动画**

   ​	首先选中一个游戏对象，然后在inspector里添加一个动画器组件。接着在Assets 里创建一个Animator 最后拖到组件对应的槽里。这个时候就需要我们打开动画窗口，如果当前带动画器的对象没有动画 它会提示你去创建Animation，若没有动画器的时候也会创建一个默认Animator。

   ​	关于创建动画， 其实就是把关键帧的sprite给拖到时间轴上进行处理。你可以通过采样的频率来控制动画的速度。同时你也可以通过它自带的一些变换来完成翻转sprite方向等功能。如果你想要看效果可以点击动画窗口上的播放键然后在scene里看。

   ​	当你创建了一部分动画之后你就要通过Animator去管理这些动画的状态变化。这个时候就需要用到Animator的窗口了, 本质上Animator是通过一个动画的状态机来控制动画切换的。主要用到的有三个部分:

   1. 用来判断状态变化的参数
   2. 动画的状态机
   3. 状态之间的过渡

     值得一提的是 虽然这个Animator窗口里有很多内容，但是最后的值和动态机以及过渡的关系设置都是在Inspector下面的， 需要点击状态和过渡去检视，具体的设置方法可以看ruby‘s adventure动画相关章节。

   ​	最后只需要在脚本里去设置和控制动画的参数就能完成动画的控制了。形如：

   ```c#
   Animator animator = GetComponent<Animator>();
   animator.SetBool("IsDestroyed", false);
   ```

    	除了利用单个参数来控制状态也可以通过两个参数来控制动画的状态，通过给不同的区间的设定不同输出来实现，比如控制人物上下左右移动时, 以水平和垂直速度作为参数来控制动画。在ruby's adventure的动画那一章有具体讲解，这里就不做赘述了

   

4. **如何创建和使用对象模板 即预设(Prefab)?**

     ​	首先是如何创建Prefab, 只需要你将层级里或者场景里的游戏对象 拖到项目界面的某个文件夹下即可生成一个预设。此时你的层级里同类型的游戏对象会变成蓝色，在检查器里会多出一个override的下拉选项，这里就是用来处理你的预设生成的实例和预设之间的变化的。override表示用选中的游戏对象的属性去覆盖预设，而revert则是回退现在游戏对象的属性到预设的状态。

     ​	想要通过生成一个实例的话，有两种方式，一是可以通过拖动项目界面里的预设到场景中，就会生成一个游戏对象实例，二是通过Instantiate方法调用来生成游戏对象实例, 示例代码如下:

     `    GameObject projectileObject = Instantiate(projectilePrefab, rigidbody2d.position + Vector2.right * 0.5f, Quaternion.identity);`

     ​	这里的这个projectilePrefab 就是一个预设的游戏对象，通过调用Instantiate方法就能生成一个该预设的游戏对象了，其他的参数则是用来调整生成对象的位置以及旋转状态。

     ​	批量生成的时候如果不对产生的对象的name属性进行操作的话 会默认的去游戏对象名字后加上(1) 这样的序号来标识游戏对象。

5. **如何使用平铺砖块(Tile)来贴图？**

     ​	第一步你需要创建一个Tilemap作为绘制的底板, 在创建的同时都会同时生成一个叫做Grid的父级对象, 这个时候你就能看见场景窗口里会变成一格格的样子了, 到时候的砖块就是要贴到这些小格子里。要想创建可以使用的砖块还得先调出画板窗口, 通过图片sprite拖到画板里来生成对应的tile。如果是一张单一的图生成一个砖块的话直接拖到画板即可，如果是多张tile在一张图片里的话，就需要在图片的检查器里设置模式 从单一变成多个，然后在sprtie editor里进行切片。然后你就会发现点开小箭头后就会从原来的一张变成好多张, 然后一起导入到画板里去。

     ​	之后的操作就十分简单了, 你就可以直接从画板里选择你想要的砖块贴到场景里的小方格里面去了。如果发现边缘没有填充的话，你需要去sprite那里去调整输入的大小 默认是100。 画板相关的一些工具就不在这里一一赘述了, 可以自行尝试。

