# SceneLoader

> 请参阅[手册/场景调度](../manual/scene-management.md)。

`SceneLoader` 组件提供加载其他场景的事件入口。

- 继承自：`MonoBehaviour`

## 序列化字段

- `string sceneName`：要加载的场景名称。

	打包时，请确认所有要加载的场景均已列入构建列表。

## 方法

- `void LoadSingle()`：切换场景。

- `void LoadAdditive()`：动态添加场景。