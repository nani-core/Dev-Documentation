# 打包

本篇手册罗列打包时的注意事项。

## 计算 shader

为了实现光学回形的检测，`Assets/Shaders/Computing Utilities` 里放了不少专门用来计算的 shader。
这些 shader 没有被任何材质引用，务必记得加到 project settings 里的 always include shaders 列表里。

## 生成建筑结构与光照烘焙

在本项目中，许多建筑结构（`MeshTile` 与 `ConcreteBox`）是程序化生成的。
为了避免将冗余的 GO 也序列化进项目，实现成了设置了 `HideFlags` 的假 gizmos。
这部分的代码可以在 `ArchitectureGenerator.cs` 里找到。

```csharp
[ContextMenu("Regenerate in Edit Mode")]
protected void RegenerateInEditMode() {
	if(Application.isPlaying)
		return;
	if(this == null)
		return;
	if(gizmosRoot == null)
		gizmosRoot = transform.Find(GizmozRootName);
	if(gizmosRoot != null) {
		DestroyImmediate(gizmosRoot.gameObject);
		gizmosRoot = null;
	}
	gizmosRoot = new GameObject(GizmozRootName).transform;
	gizmosRoot.SetParent(transform, false);
	gizmosRoot.gameObject.isStatic = gameObject.isStatic;
	Construct(gizmosRoot, InstantiateGizmos);
	gizmosRoot.MakeUntouchable();	// Here.
	gizmosRoot?.gameObject?.SetActive(enabled);
}
```

这样做有一个问题：会导致打包后的光照不正确，漏光的解决只在 editor 里有效。
这是因为，编译后的 Unity 运行时并不支持任意数量的全局动态光照（与之相反，editor 里使用的则是不计成本的策略），
所有非烘焙（baked）的 `ReflectionProbe` 都会在运行时失效（也不是所有但 practically yes）。
而要一个实体要想烘焙进 probe 的贴图里，就要在 build 时“有效”。
可惜，在 Unity 的设定里，一切设置了 `HideFlags` 的 GO 都会被算作“无效”。
最后 build 出来就表现得所有 probe 都没起作用，光照一塌糊涂。

对这个问题的暂时解决办法是 build 前先把 `ArchitectureGenerator.cs` 里的这行代码注释掉，build 完再改回去。
如果不改回去的话就会导致所有假 gizmos 显示在 hierarchy 里且保存到场景文件里，非常狗屎。

## 缺省材质

有时会发生 editor 里看着好好的，build 完后材质突然崩了的情况。

![](../public/exposed-concrete-box.png)

这是因为动态生成的 renderer 没有赋予材质的缘故。

在 editor 里，所有通过 GUI 创建的物体都会被赋予当前 RP 的默认材质。
但这种特权仅存在于 editor 里，build 后的缺省材质槽就真的是空的了，所以会显示出来纯色 magenta。

这个问题的解决方法是——手动挡上。
希望游戏程序自动填补所有缺失材质是不现实的。