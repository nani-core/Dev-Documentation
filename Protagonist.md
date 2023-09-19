# Protagonist

`Protagonist` 是主角的控制器类，为玩家控制的主角提供运动与交互功能。
这是一个单例类，任意时刻只应当至多存在一个实例。

- 继承自：`MonoBehaviour`
- 必需组件：[`ProtagonistInputHandler`](ProtagonistInputHandler), [CharacterController](https://docs.unity3d.com/ScriptReference/CharacterController.html)

## 序列化字段

### 形状

- `float height`：高度。
- `float radius`：半径。
- `Transform eye`：眼部变换。

	此变换会随视角俯仰而旋转，而主角本身不会。
	> 主摄像机对象应挂载于此变换下。

- `float eyeHanging`：眼部低于头顶的距离。

在编辑模式下修改形状字段时，主角碰撞体的实际形状会随着改变。

### 物理

- `CharacterController characterController`：控制运动的 `CharacterController` 组件。

	> 此 Unity 自带的角色控制器对于简单需求非常稳定，但若有复杂需求就显得捉襟见肘了。后面可能会考虑换成别的控制方案。

### 控制

- `float walkingSpeed`：行走速率增益。
- `float sprintingSpeed`：疾跑速率增益。
- `float orientingSpeed`：视角转动速率增益。

### 交互

- `float maxInteractionDistance`：最大交互距离。

	以眼部为计算距离的原点。

- `Image focusUi`：显示准星的 Image 组件。
- `FocusUiMap focusUiMap`：各状态下准星的样式。
	- `Sprite normal`：正常状态的准星 sprite。
	- `Sprite hovering`：视线选中可交互对象时的准星 sprite。
	- `Sprite grabbing`：抓住对象时的准星 sprite。
- `float grabbingTransitionDuration`：抓取对象归正到视野中央的时间，以秒记。
- `float grabbingEasingFactor`：抓取对象归正到视野中央的缓动程度。

	在 \[0, 1\] 间取值。数值越小，归正运动越接近线性。

### 声音

- `AudioSource sfxAudioSource`：播放玩家音效的 `AudioSource`。
- `AudioClip onFocusSound`：选中可交互对象时播放。
- `AudioClip onGrabSound`：抓起可交互对象时播放。
- `AudioClip onDropSound`：放下可交互对象时播放。
- `AudioSource footAudioSource`：播放脚步音效的 `AudioSource`。
- `List<AudioClip> stepAudioClips`：走路时播放的脚步音效，会根据移动速度改变播放频率。

## 属性

### 控制

- `Transform Eye { get; }`：眼部变换。
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

## 方法

### 控制

- `void OrientDelta(Vector2 delta)`：使朝向发生指定差值的旋转。

	输入为一二维向量，分量均为弧度制。
	X 分量表示方位角的差值，Y 分量表示眼部天顶角的差值。

	> 此方法通常由 `ProtagonistInputHandler` 调用。

- `void MoveVelocity(Vector2 vXy)`：使发生给定速度对应的瞬时运动。

	输入为一二维向量。
	X 分量表示朝主角身体（非眼部）前方（局部 Z+）的速度，Y 分量表示朝主角右方（局部 X+）的速度。

	输入会被主角的移动速率增益影响，且会自动随物理帧间隔缩放。

	> 此方法通常由 `ProtagonistInputHandler` 调用。

### 交互

- `void Interact()`：做出交互。

	当抓取着可抓取对象时，会把它放下；否则，会与选中的可交互对象交互。

- `void GrabbingOrientDelta(float delta)`：使抓取着的对象发生指定差值的 Y 轴旋转。

	> 此方法通常由 `ProtagonistInputHandler` 调用。