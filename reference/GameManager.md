# GameManager

> 请参阅[手册/生命周期总览](../manual/life-cycle-overview.md)。

`GameManager` 是游戏管理器类，负责整个游戏的生命周期以及重要对象实例的管理。

> 不应将某个具体关卡等*不亘穿整个游戏生命周期*的对象的状态交由本类来管理。

任意时刻应当存在且仅存在本类的唯一实例。
若实例初始化时发现世界中已经存在其他实例，会立即自毁；时机先于 `Start`。

`GameManager` 的实例会在初始化后将自己置为 `DontDestroyOnLoad`。

游戏结束时，`GameManager` 会释放所有池化的资源。
这主要是为了开发时不造成内存泄漏的考虑。

- 继承自：`MonoBehaviour`

## 序列化字段

- `Camera mainCamera`：主摄像机。

	在 [`Protagonist`](Protagonist.md) 初始化完成后，主摄像机会被绑定于主角的眼部变换下；
	同理，在其销毁之前，主摄像机会原地解放。

## 字段

- `RenderTexture WorldView`：主摄像机看到的世界画面。

	此材质是实现[光学回形](../manual/optical-loopshape.md)的重要基础。

- `Protagonist Protagonist`：当前世界中存在的 `Protagonist` 唯一实例。