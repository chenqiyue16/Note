# Note  
```c#
const string CACHE_VERSION = "V1";  
var serializedGuid = new List<string>();  
var serializedDependencyHash = new List<string>();  
var serializedDenpendencies = new List<int[]>();  
  
//序列化  
using (FileStream fs = File.OpenWrite(CACHE_PATH))  
{  
	BinaryFormatter bf = new BinaryFormatter();  
	bf.Serialize(fs, CACHE_VERSION);  
	bf.Serialize(fs, serializedGuid);  
	bf.Serialize(fs, serializedDependencyHash);  
	bf.Serialize(fs, serializedDenpendencies);  
}  
  
//反序列化  
using (FileStream fs = File.OpenRead(CACHE_PATH))  
{  
	BinaryFormatter bf = new BinaryFormatter();  
	string cacheVersion = (string) bf.Deserialize(fs);  
	serializedGuid = (List<string>) bf.Deserialize(fs);  
	serializedDependencyHash = (List<string>) bf.Deserialize(fs);  
	serializedDenpendencies = (List<int[]>) bf.Deserialize(fs);  
}  
```


