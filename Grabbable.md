# Grabbable

`Grabbable` 是使对象能够被主角抓起的可交互组件类。

被抓起的对象会在玩家视野中心到物体锚点的连线被遮挡时自动放下。

- 继承自：[Interactable](Interactable.md)

## 序列化字段

- `UnityEvent onGrabBegin`：被主角抓起时触发的字段。
- `UnityEvent onGrabEnd`：被主角放下时触发的字段。