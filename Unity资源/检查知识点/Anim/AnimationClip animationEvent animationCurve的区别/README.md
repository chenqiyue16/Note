# Note
AnimationClip  
AnimationClip是Unity3D中播放动画的最基本对象，通过FBX导入的各个动画对象其实就是一个AnimationClip。这个类已关键帧的形式记录了骨骼关节在各个时间节点上的位置、旋转信息，根据帧频率frameRate结合播放模式wrapMode通过插值计算即可播放出连续的骨骼动画。  
  
  
AnimationState  
每个AnimationState包含了一个AnimationClip，并记录这个动画片段的一些播放控制属性，实际上是一个AnimationClip的包装器。  
  
  
AnimationEvent  
在AnimactionCurve的某一帧上面挂载一个脚本函数，执行到这一帧时触发。动画事件函数支持0参数或一个参数，参数可以是浮点型，字符串，object或AnimationEvent。  
  
  
AnimationCurve  
生成动画剪辑的曲线的集合，存储关键帧信息。  

