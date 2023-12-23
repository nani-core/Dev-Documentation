# DtCarrier

> `DtCarrier` 脱胎于曾经的 `AutomaticDoor`，用来控制自动门的开关。

`DtCarrier` 是可以在两个状态间来回切换的载体。
被切换时，控制对象会以线性的速率在指定的两个 transform 间插值运动。

类名中的 `Dt` 取自双掷开关（double-throw switch）的隐喻。
此类 `Carrier` 的两个状态亦分别成为“开启”和“关闭”状态。

> 计划支持缓动效果。

- 继承自：[`Carrier`](./Carrier.md)

## 序列化字段

- `AudioClip movingSound`：移动时的音效。

	在移动过程中循环播放。
	**此字段功能现未予实现。**

- `AudioClip onClosedSound`：关闭时的音效。

	仅会在完全关闭的瞬间播放。

- `Transform closedTransform`：关闭时的变换。

	不得是目标的子变换。

- `AudioClip onOpenedSound`：打开时的音效。

	仅会在从完全关闭的状态打开的瞬间播放。

- `Transform openedTransform`：打开时的变换。

	不得是目标的子变换。

- `bool isOpened`：开始时是否关闭。

	在编辑模式下修改此字段时，目标会变换到正确的状态。

- `float openingDuration`：切换状态所需要的时间，以秒记。

## 属性

- `bool IsOpened { get; set; }`：是否开启。

	给此字段赋值并不会立即使得字段的读取值改变。
	字段读取值要等到完成运动后才会改变。

## 方法

- `void ToggleOpeningState()`：切换开启状态。

	在动作过程中调用此方法无效。