# Note
以下是从L18每日资源静态检查里面提炼出的一些比较通用的检查case。
资源检查还是与引擎和项目本身的开发流程强相关的，具体的实现还是要结合项目本身。
一方面要多了解平时各职能的资源制作流程，从中思考可以检查的点；另一方面要对产生的功能bug追根溯源，根据原因思考是否可以增加每日静态检查。


文件通用：
	文件meta的guid重复检查
	文件大小检查（如场景<30M，动作小于20M等）
	文件特殊格式检查（一些引擎内不会用到的文件 .max .can3 .dds .3ds等）
	文件约定格式检查（如与美术策划约定好的 materia文件夹只能放材质，prefab文件夹只能放prefab等）
	文件命名检查（如名字不能包含中文、特殊符号等）
	文件同目录下不同扩展名的同名文件检查（如test.tga和test.png）

预制体通用：
	预制体中脚本为空检查
	预制体根节点未激活检查
	预制体命名检查（预制体名字不能包含中文、特殊符号，预制体每个节点不能包含中文、特殊符号、不能有missing等）
	预制体引用的材质球丢失
	根据游戏实际情况扩展各种预制体的XX节点引用丢失（如mesh、renderer、modelslot等节点不能为空）

材质通用：
	角色、场景、特效、UI等材质球的贴图丢失
	角色、场景、特效、UI等材质球不能使用纯色贴图
	角色、场景、特效、UI等材质球的shader不能使用默认（如Unity的standard）

贴图通用：
	角色、场景、特效、UI等不同类型贴图尺寸、IOS/安卓压缩格式检查

角色：
	角色模型面数（三角形数）超标检查
	角色模型骨骼数超标检查
	角色动作的内存超标检查
	角色动作文件不能有mesh的检查
	角色模型常规设置检查（如模型可读写、collider、模型某些节点配置等，具体要结合引擎以及策划、程序、技美的需求来定规则）

特效：
	特效存在时间（startLifetime）超标检查
	特效文件只有一个mesh、一个renderer的检查
	特效模型常规设置检查（如模型可读写、collider、模型某些节点配置等，具体要结合引擎以及策划、程序、技美的需求来定规则）

UI：
	UI预制体引用图集个数上限（如一个预制体的图集个数<5）
	UI预制体字体检查
	UI预制体文字层级检查（如文字层级要高于图片层级，便于减少dc）
	UI的按钮组件丢失Collider检查

场景：
	场景节点中包含空脚本检查
	场景节点内模型的面数检查
	场景内网格丢失检查
	场景内路点等坐标都应该在网格内的检查
	检查场景位置不能在（0，0，0）点的检查
	场景内节点不能引用另一个场景内的节点检查（不然会导致场景进bundle过大）
