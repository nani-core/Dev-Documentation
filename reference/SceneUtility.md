# SceneUtility

`SceneUtility` 是提供场景辅助功能的静态工具类。

## 方法

- `static AsyncOperation LoadSceneByNameAsync(string sceneName, LoadSceneMode mode)`：以指定的模式加载场景。
	- `string sceneName`：场景名。
	- `LoadSceneMode mode`：加载模式。

	本方法允许在编辑器里加载未列入构建列表的场景，同时对打包友好。