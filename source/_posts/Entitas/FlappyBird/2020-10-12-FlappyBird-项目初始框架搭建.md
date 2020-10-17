---
title: FlappyBird之项目初始框架搭建
---

 
## 导入Entitas插件
创建一个Unity空项目，然后导入Entitas-1.13.0.unitypackage资源文件 [附包下载地址](https://longshilin.com/files/Entitas-1.13.0.unitypackage)

Entitas插件导入之后，按快捷键 `Ctrl + Shift + G` 生成Generated文件目录，再创建一个Features目录存放游戏逻辑代码，Scenes存放场景资源文件。

最终框架结构如下：
![](https://cdn.jsdelivr.net/gh/longshilin/images/20201012155210.png)

## 接入框架驱动类
通过MonoBehavior的生命周期函数驱动框架内的游戏控制器。

`GameControllerBehavior.cs`
```c#
using System;
using UnityEngine;

public class GameControllerBehaviour : MonoBehaviour
{
    private GameController _gameController;

    private void Awake()
    {
        _gameController = new GameController(Contexts.sharedInstance);
    }

    private void Start()
    {
        _gameController.Initialize();
    }

    private void Update()
    {
        _gameController.Execute();
    }
}
```

`GameController.cs`
```c#
using Entitas;

/// 游戏控制器
/// 管理游戏的总入口
public class GameController
{
    private readonly Systems _systems;
    private readonly Contexts _contexts;

    public GameController(Contexts contexts)
    {
        _contexts = contexts;
         _systems = new GameSystems(_contexts);
    }

    public void Initialize()
    {
        _systems.Initialize();
    }

    public void Execute()
    {
        _systems.Execute();
        _systems.Cleanup();
    }
}
```

`GameSystem.cs`
```c#
/// 游戏系统控制器
/// 管理游戏内所有System的创建和实例化
public class GameSystems : Feature
{
    public GameSystems(Contexts contexts)
    {
        // create all systems
    }
}
```

上面三个类实现初始化所有Systems，并从MonoBehavior中驱动所有的Systems。

