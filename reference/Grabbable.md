# Grabbable

`Grabbable` 是使对象能够被抓起的功能组件类。

被抓起的对象会在准星连线被遮挡时自动放下。

- 继承自：`MonoBehaviour`

## 序列化字段

- `UnityEvent onGrabBegin`：被抓起时触发的字段。
- `UnityEvent onGrabEnd`：被放下时触发的字段。

## 方法

- `void Grab()`：使被抓起。

	若已经有另外的物体被抓起，则会先放下该物体。

	即使调用时实际不满足抓取条件，也会强制抓起。
	抓起后一帧可能会检测到不满足条件，然后立即被动放下。
	不过此接口通常是由 `Protagonist` 在合适的时候调用，因此不会出问题。

- `void Drop()`：使被放下。

	若未被抓起，调用此方法不会有任何后果。