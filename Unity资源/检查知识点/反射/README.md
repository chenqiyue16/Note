# 反射
```c#
    Type type = typeof(AutoQAChecker)
    // 反射根据名称拿某个method
    MethodInfo methodInfo = type.GetMethod(methodName, BindingFlags.NonPublic | BindingFlags.Public | BindingFlags.Static);
    
    // 反射拿全部method
    MethodInfo[] methodInfos = type.GetMethods(BindingFlags.NonPublic | BindingFlags.Public | BindingFlags.Static);
    
    // 反射拿property 和 field的区别： 带get方法的属性叫property，没有get方法的字段叫field
    //GetFields会自动获得子类与父类的所有字段，因此需要加BindingFlags ：DeclaredOnly 
    PropertyInfo[] propertyInfos = type.GetProperties();
    PropertyInfo propertyInfo = type.GetPropertie(propertyName);
    FieldInfo[] fieldInfos = type.GetFields();
    FieldInfo fieldInfos = type.GetField(fieldName);
 
    // 反射拿值
    // 正常拿一个对象的值，需要传这个对象进去
    foreach (var item in configList)
    {
        fieldInfo.GetValue(item);
    }
    
    // static静态取值 比如有一个叫ConfigList的property 记录了一些配置的list，并且是static的方法，GetValue没法传值
    ordinaryConfigList[i].GetProperty("ConfigList").GetValue(null)
    
    // 枚举取值，同样要传null
    otherNameTempInfo.GetValue(null);
```