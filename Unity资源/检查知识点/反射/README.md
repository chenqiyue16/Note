﻿# 反射
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
    
    c#反射查找方法时，默认只能查到public方法。如果想要查找private方法，需要设定BindingFlags.

    即：

    BindingFlags.Public|BindingFlags.Instance 默认查找public、instance内容

    BindingFlags.NonPublic|BindingFlags.Instance 查找nonpublic、instance内容

    另外，BindingFlags.Instance和BindingFlags.Static二者必须有一项或者都有。如果你的类是instance，就选instance，反之选static。如果两者都不选，是找不到任何方法的

    BindingFlags枚举值：

    BindingFlags.IgnoreCase：表示忽略 name 的大小写，不应考虑成员名的大小写

    BindingFlags.DeclaredOnly：只应考虑在所提供类型的层次结构级别上声明的成员。不考虑继承成员。

    BindingFlags.Instance：只搜索实例成员

    BindingFlags.Static：只搜索静态成员

    BindingFlags.Public：只搜索公共成员

    BindingFlags.NonPublic：只搜索非公共成员

    BindingFlags.FlattenHierarchy：应返回层次结构上的公共静态成员和受保护的静态成员。不返回继承类中的私有静态成员。静态成员包括字段、方法、事件和属性。不返回嵌套类型。

    BindingFlags.InvokeMethod：表示调用方法，而不调用构造函数或类型初始值设定项。对 SetField 或 SetProperty 无效。

    BindingFlags.CreateInstance：表示调用构造函数。忽略 name。对其他调用标志无效。

    BindingFlags.GetField：表示获取字段值。

    BindingFlags.SetField：表示设置字段值。

    BindingFlags.GetProperty：表示获取属性。

    BindingFlags.SetProperty：表示设置属性。
```
