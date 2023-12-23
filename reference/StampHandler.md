# StampHandler

`StampHandler` 是用来在运行时实现「投射」操作的代理类。
开发者不应当手动将其添加至场景中。

被投射的每个带有 `MeshRenderer` 的 `GameObject` 将会生成一个此类实例。
它可以管理投射材质，使其在销毁/还原时自动被释放。

> 事实证明这玩意不太好用，将会考虑用静态外部类上位替代。

- 继承自：`MonoBehaviour`

## 字段

- `Material Material`：当前使用的材质。

	可能是投射过的材质，或者是原本的材质。

## 方法

- `static void Stamp(GameObject target, Camera camera)`：
	将某相机的画面投射到某物体上。

	本方法是公有静态方法，设计出来就是让外部模块调用的。

	调用此方法会自动在目标物体上生成本类实例。

- `void Initialize()`：用来在脚本中创建后代替 `Start()` 执行。

	此方法必须在调用其他方法（包括字段）之前执行。
	`Start()` 中会免重复地调用。

- `void SetStampedState()`：标记投射状态，并记录原本的材质。

	如果已经标记过，不会重复标记。

- `void Restore()`：还原初始材质，清除投射状态。

- `void SetStampingTexture(RenderTexture texture)`：使用传入的材质作为投射材质。

	调用此方法会自动标记投射状态。
	重复投射不会覆盖原本材质。