# Detachable

`Detachable` 是赋予物体*解体*的功能组件类。

`Detachable` 必须作用在 `Rigidbody` 上。
在 `Detachable` 方法被调用后，自身的 hierarchy 将会被移动到最近的 static 父级 `Transform` 下，然后将 `Rigidbody` 的 `isKinematic` 关闭。

注意，`Detachable` 不会在 `Start` 时自动开启 `Rigidbody` 的 `isKinematic` 选项。
这一步需要关卡设计师手动完成。

- 继承自：`MonoBehaviour`
- 必需组件：`Rigidbody`

# 序列化字段

- `bool useDetachingEjection`：解体时是否获得初速度。
- `Vector3 ejectionVelocity`：解体时获得的速度，相对于对象局部坐标。
- `Vector3 ejectionOrigin`：解体时获得速度的受力位置，相对于对象局部坐标。
- `UnityEvent onDetached`：解体时触发的事件。

# 方法

- `void Detach()`：使解体。

	解体后，此组件自身会切换至禁用状态。