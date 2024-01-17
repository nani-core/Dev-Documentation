# LevelLoader

> 请参阅[手册/场景调度](../manual/scene-management.md)。

`LevelLoader` 组件提供加载其他关卡的事件入口。

- 继承自：`MonoBehaviour`

## 序列化字段

- `Level template`：要加载的关卡模板（prefab）。

## 方法

- `void InstantiateLevelAtPlace()`：以自己为基准实例化关卡模板。

- `void InstantiateLevelAt(Transform place)`：在基准变换处实例化关卡模板。

- `void InstantiateLevelAtSpawnPoint()`：实例化关卡模板，使得主角在不动的情况下正好与关卡实例的出生点对齐。