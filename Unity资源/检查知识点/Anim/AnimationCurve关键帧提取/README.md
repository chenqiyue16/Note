# Note
```c#
 //存储所有的关键帧信息  
 Keyframe[] kFrames;  
 AnimationClip animationClip = currentCheckAnimationClip.Clip;  
 foreach (var curveBinding in AnimationUtility.GetCurveBindings(clip))  
 {  
    //每个CurveBinding去拿相应的曲线信息和关键帧  
    var curve = AnimationUtility.GetEditorCurve(animationClip, curveBinding);  
	kFrames = curve.keys;  
	string propertyName = curveBinding.propertyName;  
	if (propertyName.Contains("MotionT.x")){  
	  //获取名为MotionT.x的曲线的第0帧的x值  
	  paoKuAnim.firstKeyFrameMotion.x = kFrames[0].value;  
	}  	
 }   
```
 