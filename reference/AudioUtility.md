# AudioUtility

`AudioUtility` 是提供声音辅助功能的静态工具类。

## 类型

- `struct AudioPlayConfig`：声音播放设置。

	### 字段

	- `FloatRange range`：声音可以被听见的距离范围。

	### 方法

	- `void ApplyOn(AudioSource source)`：应用设置于 `AudioSource` 上。

## 方法

- `static IEnumerator PlayOneShotAtCoroutine(AudioClip clip, Vector3 worldPosition, Transform under)`
- `static IEnumerator PlayOneShotAtCoroutine(AudioClip clip, Vector3 worldPosition, Transform under, AudioPlayConfig config)`：生成在某位置播放一次音效的协程。

	- `AudioClip clip`：要播放的音效。
	- `Vector3 worldPosition`：位置。
	- `Transform under`：跟随变换。若不需要，传入 `null`。
	- `AudioPlayConfig config`：播放设置。