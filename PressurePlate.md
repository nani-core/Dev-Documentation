# PressurePlate

`PressurePlate` 是压力板的控制器类。

- 继承自：`MonoBehaviour`
- 必需组件：`Collider`

## 序列化字段

- `Transform plate`：压力板可压下的板子。
- `float sinkingDistance`：被按下时，板子下沉的距离，局部坐标。
- `List<GameObject> targets`：可以按下该压力板的对象。
- `AudioClip onPressedSound`：按下时的音效。
- `UnityEvent onPressed`：按下时触发。
- `AudioClip onReleasedSound`：抬起时的音效。
- `UnityEvent onReleased`：抬起时触发。

## 属性

- `bool Pressed { get; set; }`：是否按下。