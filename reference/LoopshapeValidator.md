# LoopshapeValidator

`LoopshapeValidator` 是回形检测器的基类。

- 继承自：`MonoBehaviour`

## 序列化字段

- `Loopshape loopshape`：对应的回形。

	可以置空，即对应自身 `GameObject` 上挂载的 `Loopshape`。

## 属性

- `Loopshape Loopshape`：`loopshape` 的访问器。

- `bool IsValid`：检测条件是否满足。