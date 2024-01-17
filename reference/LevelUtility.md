# LevelUtility

> 请参阅[手册/场景调度](../manual/scene-management.md)。

`LevelUtility` 是提供场景辅助功能的静态工具类。

## 方法

- `static Level InstantiateLevelFromTemplate(this Level template, Vector3 position, Quaternion orientation)`
- `static InstantiateLevelFromTemplate(this Level template, Transform place)`：实例化关卡并设置基准变换。

- `static Level InstantiateLevelFromTemplateAtSpawnPoint(this Level template)`：实例化关卡并使其出生点对齐主角。

- `static void DestroyEveryLevelInstanceOfTemplate(this Level template)`：销毁关卡模板的所有实例。