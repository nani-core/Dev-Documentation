# Protagonist

`Protagonist` 是主角的控制器类，为玩家控制的主角提供运动与交互功能。
这是一个单例类，任意时刻只应当至多存在一个实例。

- 继承自：`MonoBehaviour`

## 序列化对象

- [`ProtagonistProfile`](ProtagonistProfile.md) `profile`：配置。

## 属性

### 控制

- `Transform Eye { get; }`：眼部变换。

	此变换朝向主角视角。

- `Vector3 Upward { get; }`：视角的上方。

	当主角仰视或俯视时，此向量会相应地倾斜。

- `bool IsOnGround { get; }`：是否着地。
- `bool IsSprinting { get; set; }`：是否疾跑。
- `float Azimuth { get; set; }`：朝向的方位角（弧度制）。

	以 Z+ 为起始，X+ 为正方向。

- `float Zenith { get; set; }`：眼部朝向的天顶角（弧度制）。

	以黄道平面为起始，Z+ 为正方向。

### 交互

- [`Interactable`](Interactable.md) `FocusingObject { get; set; }`：被视线选中的可交互对象。

	将此属性设为 `null` 以取消选中。

- [`Grabbable`](Grabbable.md) `GrabbingObject { get; set; }`：被抓取的可抓取对象。

	> 通常不会出现在抓着甲时直接换成乙的情况，会先放下甲再抓起乙。

	抓起时，抓取对象的变换会被移到眼部变换下，然后经历一个 `grabbingTransitionDuration` 所指定时长的归正运动；其锚点平移至视角中心（起始与终止位置距离眼部的距离相等），局部 Y 轴与眼部 Y 轴对齐。

	将此属性设为 `null` 以放下当前抓取对象。

	放下时，抓取对象的变换会恢复到抓取前的父变换下（若是可解体的则会成为野生变换）。

- `bool GrabbingOrienting { get; set; }`：是否在旋转抓取对象。

	旋转抓取对象时，玩家无法主动改变主角视角，但仍可移动。

	未抓取对象时，此属性固定为 `false`。

- `LoopShape SatisfiedLoopShape { get; }`：当前满足的回形图案。

## 方法

### 控制

- `void OrientDelta(Vector2 delta)`：使朝向发生指定差值的旋转。

	输入为一二维向量，分量均为弧度制。
	X 分量表示方位角的差值，Y 分量表示眼部天顶角的差值。

	> 此方法通常由 `ProtagonistInputHandler` 调用。

- `void MoveVelocity(Vector2 vXy)`：使发生给定速度对应的瞬时运动。

	输入为一二维向量。
	X 分量表示朝主角身体（非眼部）前方（局部 Z+）的速度，Y 分量表示朝主角右方（局部 X+）的速度。

	输入会被主角的移动速率增益影响，且会缓冲到下一物理帧生效。

	离地时无效。

	> 此方法通常由 `ProtagonistInputHandler` 调用。

- `void MoveDelta(Vector2 vXy)`：使发生指定距离的运动。

	输入为一二维向量。
	X 分量表示朝主角身体（非眼部）前方（局部 Z+）的距离，Y 分量表示朝主角右方（局部 X+）的距离。

	输入会被主角的移动速率增益影响，且会缓冲到下一物理帧生效。

	离地时无效。

	> 讨论：此方法的效果是否不应受到移动速率增益影响？

- `void Jump()`：跳跃。

	离地时无效。

### 交互

- `void Interact()`：做出交互。

	当抓取着可抓取对象时，会把它放下；否则，会与选中的可交互对象交互。

- `void GrabbingOrientDelta(float delta)`：使抓取着的对象发生指定差值的 Y 轴旋转。

	> 此方法通常由 `ProtagonistInputHandler` 调用。