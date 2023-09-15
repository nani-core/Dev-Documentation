# Waterlet

`Waterlet` 是水口的控制器基类。
水口可以开启或关闭，开启的水口会影响水体（[Water](Water.md)）的高度。

- 继承自：`MonoBehaviour`
- `abstract`

## 序列化字段

- `Water water`：目标水体。
- `Transform pivot`：“流水点”变换。

	调整此变换的局部位置以支持不同形态的水口。

- `bool active`：游戏开始时水口是否开启。

## 属性

- `bool IsActive { get; set; }`：运行时水口是否开启。

	> 此属性正在考虑由 `MonoBehaviour.enabled` 替代！

- `float Height { get; }`：水口相对于水体底面的高度。

## 方法

- `void ToggleActive()`：切换水口的开启状态。