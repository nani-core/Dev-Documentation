# FocusUi

`FocusUi` 是主角交互焦点 UI（即「准星」）的控制器类。
本类实例应序列化于 [`ProtagonistProfile`](ProtagonistProfile.md) 的 `interactionUiPrefab` 所对应的 prefab 中，[`Protagonist`](Protagonist.md) 会在初始化时自动生成并获取正确的引用。

- 继承自：`MonoBehaviour`

## 序列化字段

- `FocusUiMap focusUiMap`：各状态下准星的样式。
	- `Sprite normal`：正常状态的准星 sprite。
	- `Sprite hovering`：视线选中可交互对象时的准星 sprite。
	- `Sprite grabbing`：抓住对象时的准星 sprite。