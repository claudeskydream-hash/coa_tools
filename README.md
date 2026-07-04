<img src="./coa_tools_logo.png" width="250">

# 剪纸动画工具（Cutout Animation Tools）- 使用文档
这是 Blender/Godot 插件 Cutout Animation Tools 的使用文档。

如果你喜欢这个插件，并愿意通过小额捐赠来支持我，欢迎点击这里：

[![](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=8TB6CNT9G8LEN)

## 简介
Cutout Animation Tools（简称 COA Tools）是一款用于 Blender 的 2D 骨骼绑定与动画套件。它提供与 Spine、Spriter 等程序类似的工具。COA Tools 让你能够在 Blender 中快速创建 2D 剪纸角色/动画。得益于 Blender 出色的动画系统与本插件的配合，你可以获得一套功能强大的 2D 动画解决方案。整套工具由 3 个不同的组件组成：Photoshop 精灵图导出器、Blender 插件、Godot 导入器。

[点击查看插件的实际演示。](https://www.youtube.com/playlist?list=PLPI26-KXCXpA-VMlDIWpmdq6M1m4LEjf_)

### Photoshop 精灵图导出器
将 Photoshop 图层快速导出为独立文件，并附带 json 坐标信息。这些数据可用于在 Blender 中极为快速地导入精灵图。
功能特性：
- 将图层导出为精灵图（sprite）
- 将包含多个图层的文件夹导出为精灵图集（spritesheet）
- 生成包含所有图层位置和精灵图集信息的 json 数据

### GIMP 精灵图导出器
将 GIMP 的图层和图层组导出为独立文件，并附带 json 坐标信息。更多使用说明请参阅 GIMP 文件夹下的 README.md。

### Cutout Animation Tools Blender 插件
这是整套工具中最大的组件，因为绝大部分工作都在这里完成。
插件提供的功能包括：
- 精灵图导入器（可导入单张或多张精灵图，或使用 json 数据作为导入依据）
- 支持网格（mesh）的动画精灵图集
- 骨架编辑——超快速的骨骼创建工具。只需绘制骨骼，再点击将精灵图附加到骨骼上
- 网格编辑——绘制顶点轮廓，并用细分网格快速填充。填充过程同时完成 UV 展开并映射纹理数据
- 权重编辑——针对细分网格的快速权重编辑
- 快速生成 IK 与拉伸（stretch to）约束
- 增强的精灵物体（sprite_object）动画处理
- 精灵物体大纲视图 -> 显示所有包含的精灵图、骨架及骨骼，便于更好、更快速地访问单个精灵图
- 正交相机操作符 -> 生成一台可用于渲染动画的正交相机。相机分辨率与精灵图的像素空间完美匹配
- json 导出 -> 将所有精灵物体数据导出为 json 文件。支持的功能包括：骨骼与精灵图层级导出、烘焙动画导出

### Godot 剪纸动画导入器
这是一个高级导入器，帮助你把从 Blender 导出的所有数据导入到 Godot 中。
功能特性：
- Json 导入器
- 精灵图、骨骼和动画均会被导入
- 智能重新导入功能。可以将你在 Godot 中所做的本地修改合并到新导入的场景中。这实现了极为灵活的工作流：在 Blender 中制作，然后导出；在 Godot 中导入；再进行诸如新增节点、添加自定义动画等扩展。启用合并后，重新导入时所有本地修改都会被保留。

## 下载与安装
将该 github 仓库下载或克隆到你的本地磁盘。如果你从 Github 下载 ZIP 文件，请务必先解压。
不要试图在 Blender 中直接安装下载的 zip 文件，这样是行不通的。解压后请按照下面的安装说明操作。

### Photoshop 导出器：

需要将 .jsx 文件复制到 Photoshop 的脚本文件夹中，其位置为：

C:\Program Files\Adobe\Adobe Photoshop CC 2015\Presets\Scripts

别忘了重启 Photoshop，然后依次进入 文件（File）-> 脚本（Scripts）-> BlenderExporter.jsx

### Krita 导出器：
启动 Krita，进入 设置（Settings）-> 管理资源（Manage Resources），在弹出的新窗口中点击“打开资源文件夹（Open Resource Folder）”。这会打开 Krita 的资源目录。如果不存在 pykrita 目录，请自行创建一个。
现在把 Github 上 Krita 目录中的全部内容复制到 pykrita 目录中。重启 Krita。
接着进入 设置（Settings）-> 配置 Krita（Configure Krita），再进入 Python 插件管理器（Python Plugin Manager），启用 COA Tools Exporter。插件激活后，你就可以在 设置（Settings）-> 停靠面板（Dockers）-> COA Tools Exporter 下启用该停靠面板。

现在只需选中你想要导出的图层，在停靠面板中定义项目名称和路径，然后导出图片即可。

### GIMP 导出器：

应将 coatools_exporter.py 复制到你的 GIMP 插件（plug-ins）文件夹中，其位置为：
- Linux：/home/YOU/.gimp2.8/plug-ins/
- Windows：C:\Users\YOU\.gimp2.8\plug-ins

重启 GIMP 后，它应会出现在 文件（Files）> 导出到 CoaTools（Export to CoaTools...） 菜单下


### Blender 插件：
将 coa_folder 压缩成 zip。
进入 文件（File）-> 用户偏好设置（User Preferences）-> 插件（Add-ons），点击“从文件安装...（Install from file...）”按钮。
这会为 Blender 安装并启用该插件。别忘了保存用户偏好设置，否则重启后插件将不会被激活。


### Godot 导入器：
请注意，该导入器仅能在当前的 godot 2.1 开发版（dev builds）中运行。
在你的游戏项目文件夹中创建一个 /addons 文件夹，并将 coa_importer 文件夹复制到该 addons 文件夹中。文件加载完成后，进入 项目设置（Project Settings）-> 插件（Plugins）-> Cutout Animation Importer，激活该插件。
