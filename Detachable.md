# Detachable

`Detachable` 是可以在主角点击交互时解体的可交互组件类。

- 继承自：[Interactable](Interactable.md)

# 序列化字段

- `bool useDetachingEjection`：解体时是否获得初速度。
- `Vector3 ejectionVelocity`：解体时获得的速度，相对于对象局部坐标。
- `Vector3 ejectionOrigin`：解体时获得速度的受力位置，相对于对象局部坐标。
- `UnityEvent onDetached`：解体时触发的事件。

# 方法

- `void Detach()`：使解体。

	解体后，此组件自身会切换至禁用状态。