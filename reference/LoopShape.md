# LoopShape

`LoopShape` 是游戏核心机制——回形——的控制器基类。

- 继承自：`MonoBehaviour`

## 序列化字段

- `UnityEvent onValidated`：满足回形时触发。

	若此回形是自然满足的，则会在开始时触发一次。

- `UnityEvent onInvalidated`：回形不再满足时触发。
- `UnityEvent onOpen`：打开回形时触发。

## 属性

- `static HashSet<LoopShape> All { get; }`：场景中所有 `LoopShape` 实例。

## 方法

- `bool Validate(Transform eye)`：从 `eye` 的视角看过去，是否满足回形？