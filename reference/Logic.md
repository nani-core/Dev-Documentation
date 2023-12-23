# Logic

`Logic` 用来实现场景可调用的逻辑。
把它挂载到 `GameObject` 上，即可在其他 `UnityEvent` 中调用。

这是一个抽象类，具体有很多种不同的逻辑行为。

- 继承自：`MonoBehaviour`

## 方法

- `void Invoke()`：调用逻辑。