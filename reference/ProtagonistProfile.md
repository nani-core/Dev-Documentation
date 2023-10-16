# ProtagonistProfile

`ProtagonistProfile` 是储存主角配置信息的数据容器类。
整个游戏应当共用同一个 `ProtagonistProfile` 实例，除非某些关卡里需要更改主角的配置（例如增大跳跃高度）。

本类实例可以由资产右键菜单 `Nani Core/Loopool/Protagonist Profile` 创建。

- 继承自：`ScriptableObject`

## 序列化字段

### 形状

- `float height`：高度。
- `float radius`：半径。
- `float eyeHanging`：眼部低于头顶的距离。

### 控制

- `InputActionAsset inputActions`：玩家输入配置表。
	- `Normal`：常态。

		- `Vector2 MoveVelocity`：移动瞬时速率。
		- `Vector2 OrientDelta`：朝向差值。
		- `Button SetSprinting`：切换奔跑状态。
		- `Button Interact`：交互。
		- `Button Chear`：风灵月影。
		- `Button Jump`：条约。
		
	- `Grabbing`：抓取物体时。
	
		- `Button SetGrabbingOrienting`：切换调整抓取物品朝向状态。

			此状态置起时，玩家不可控制主角朝向。

- `float skinDepth`：碰撞检测时的容错厚度。
- `float walkingSpeed`：行走速率增益。
- `float sprintingSpeed`：疾跑速率增益。
- `float acceleration`：加速系数。

	越低的加速系数，主角从静止加速到预期速度就越慢。

- `float stepDistance`：跬距。

	此值会影响走路音效的播放频率。

- `float orientingSpeed`：视角转动速率增益。
- `float jumpingHeight`：跳跃高度。
- `float stepHeight`：可自动迈过的最大高度。

### 交互

- [`FocusUi`](FocusUi.md) `interactionUiPrefab`：交互 UI prefab。
- `float maxInteractionDistance`：最大交互距离。

	以眼部为计算距离的原点。

- `float grabbingTransitionDuration`：抓取对象归正到视野中央的时间，以秒记。
- `float grabbingEasingFactor`：抓取对象归正到视野中央的缓动程度。

	在 \[0, 1\] 间取值。数值越小，归正运动越接近线性。

### 声音

- `AudioSource sfxAudioSource`：播放玩家音效的 `AudioSource`。
- `AudioClip onFocusSound`：选中可交互对象时播放。
- `AudioClip onGrabSound`：抓起可交互对象时播放。
- `AudioClip onDropSound`：放下可交互对象时播放。
- `AudioSource footAudioSource`：播放脚步音效的 `AudioSource`。
- `List<AudioClip> stepAudioClips`：走路时播放的脚步音效，会根据移动速度改变播放频率。