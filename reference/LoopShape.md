# LoopShape

`LoopShape` 是游戏核心机制——回形——的控制器基类。

- 继承自：`MonoBehaviour`

## 序列化字段

- `UnityEvent onSatisfy`：制造回形条件开始满足时触发。

	若此回形是自然满足的，则会在开始时触发一次。

- `UnityEvent onUnsatisfy`：制造回形条件不再满足时触发。
- `UnityEvent onOpen`：回形被激活时触发。

## 属性

- `static HashSet<LoopShape> All { get; }`：场景中所有 `LoopShape` 实例。

## 方法

- `bool Satisfied(Transform eye)`：从 `eye` 的视角看过去，是否满足制造回形的条件？