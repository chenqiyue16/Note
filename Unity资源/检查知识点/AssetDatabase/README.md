# Note  
AssetDatabase.FindAssets() 直接获取Assets下所有文件路径，速度比较快  
AssetDatabase.GetAssetPath(Gameobject obj) 直接获取某个gameObject对应的文件路径  
AssetDatabase.GUIDToAssetPath(string guid) 通过guid获取文件路径  
AssetDatabase.AssetPathToGUID(string path) 通过文件获取GUID  
AssetDatabase.GetAssetDependencyHash(string path) 获取文件的哈希值，如果此哈希值发生变化，说明资源已更改  
AssetDatabase.GetDependencies(string pathNames, bool recursive) 获取一个资源的所有直接依赖关系，recursive为true时递归获取全部依赖关系  
