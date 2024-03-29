# Water

`Water` 是水体的控制器类。
挂载了此类控制器的游戏对象，可以使可漂浮对象（[Floatable](Floatable.md)）漂浮，并受到水口（[Waterlet](Waterlet.md)）的控制改变水面高度。

- 继承自：`MonoBehaviour`
- 必需组件：`BoxCollider`
	> 这里只能用 `BoxCollider` 是因为 Unity 内建的水面只支持此种碰撞体。
	> 若能够找到上位替代，以后会考虑替换。

## 序列化字段

- `Transform surface`：水面变换。

	在控制此水体的水口开启或关闭时，水面的高度会动态改变。

- `float height`：默认水面高度（局部 Y）。

- `float speed`：水面升降的速度（局部 Y/秒）。

- [WaterProfile](WaterProfile.md) `profile`：水体的物理配置。

## 属性

- `float Height`：水面的世界坐标高度。

	改动此属性导致的水面高度变化是瞬时的。
	若想连续变化，请设置 `TargetHeight`。

- `float TargetHeight`：水面的目标高度。

## 方法

- `void AddWaterlet(Waterlet waterlet)`：添加水口。
- `void RemoveWaterlet(Waterlet waterlet)`：移除水口。
- `void UpdateTargetHeight()`：根据水口自动设置目标高度。