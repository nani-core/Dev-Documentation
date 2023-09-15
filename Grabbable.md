# Grabbable

`Grabbable` 是使对象能够被主角抓起的可交互组件类。
相较于其他可交互组件，它多了两个 `OnGrabBegin`、`OnGrabEnd` 消息，分别在被主角抓起和放下时触发。

- 继承自：[Interactable](Interactable.md)

## 序列化字段

- `UnityEvent onGrabBegin`：被主角抓起时触发的字段。
- `UnityEvent onGrabEnd`：被主角放下时触发的字段。