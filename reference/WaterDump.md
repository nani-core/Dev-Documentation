# WaterDump

`WaterDump` 是排水口的控制器类。
在目标水体没有注水口开启时，挂载有此类组件的对象在启用时可以使水体下降到至少与自身齐平的高度。

- 继承自：[`Waterlet`](Waterlet.md)

## 序列化字段

- `Renderer swirl`：展示漩涡的渲染器组件。

	在水面高于自身且开启时，漩涡会不停旋转以示玩家此排水口正在工作；
	否则，漩涡不显示。

	> 旋转漩涡只是暂时的视觉呈现方案，将来会更新。