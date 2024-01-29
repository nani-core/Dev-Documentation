# Loopshape

`Loopshape` 是游戏核心机制——回形——的控制器基类。

- 继承自：`MonoBehaviour`

> 请参阅[手册/回形](../manual/loopshape.md)。

## 序列化字段

- `UnityEvent onOpen`：打开回形时触发。

## 属性

- `bool IsValid`：检测条件是否满足。

## 方法

- `void Open()`：触发打开事件。

- `void Hollow()`：在环上挖一个岛形状的洞。

	只有检测器为 `OpticalValidator` 时，此方法才有效。