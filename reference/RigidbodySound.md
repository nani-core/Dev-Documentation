# RigidbodySound

> 请参阅[手册/声音](../manual/audio.md)。

`RigidbodySound` 是为刚体配音的控制器类。

- 继承自：`MonoBehaviour`
- 必需组件：`RigidBody`

## 序列化字段

- `float minCollideSpeed`：触发碰撞音效的最小相对速度。
- `AudioClip[] onCollide`：碰撞时播放。
- `AudioClip[] onEnterWater`：入水时播放。
- `AudioClip[] onLeaveWater`：出水时播放。

## 方法

- `void PlaySound(AudioClip clip)`
- `void PlaySound(AudioClip clip, Vector3 worldPosition)`：在指定位置播放音效。

	播放时，音效跟随自身运动。

	若不指定位置，默认是在自身的锚点。