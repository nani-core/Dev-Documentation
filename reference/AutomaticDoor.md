# AutomaticDoor

`AutomaticDoor` 是自动门的控制器类。
当门被开启/关闭时，它会以稳定的速度线性变换到目标状态。

- 继承自：`MonoBehaviour`

## 序列化字段

- `Transform door`：可移动的门板。
- `AudioClip movingSound`：移动时的音效。

	此字段功能现未予实现。

- `AudioClip onClosedSound`：关闭时的音效。

	仅会在完全关闭的瞬间播放。

- `Transform closedTransform`：关闭时的变换。

	不得是门板的子变换。

- `AudioClip onOpenedSound`：打开时的音效。

	仅会在从完全关闭的状态打开的瞬间播放。

- `Transform openedTransform`：打开时的变换。

	不得是门板的子变换。

- `bool isOpened`：开始时是否关闭。

	在编辑模式下修改此字段时，门板会变换到正确的状态。

- `float openingDuration`：切换状态所需要的时间，以秒记。

## 属性

- `bool IsOpened { get; set; }`：是否开启。

	给此字段赋值并不会立即使得字段的读取值改变。
	字段读取值要等到门板完成其动作后才会改变。

## 方法

- `void ToggleOpeningState()`：切换开启状态。

	在动作过程中调用此方法无效。