# 开发文档

## Manual / 手册

- [生命周期总览](manual/life-cycle-overview.md)（待编撰）
- [回形与交互](manual/loopshape-and-interaction.md)
- [相机与渲染](manual/camera-and-rendering.md)
- [声音](manual/audio.md)
- [场景搭建](manual/architecture.md)（待编撰）
- [场景调度](manual/scene-management.md)
- [打包](manual/building.md)
- [Git 仓库管理](manual/git-repository-management.md)
- [建模](manual/modelling.md)

## Reference / 参考

- [GameManager](reference/GameManager.md) / 游戏管理器

### Protagonist / 主角

- [Protagonist](reference/Protagonist.md) / 主角
- [ProtagonistProfile](reference/ProtagonistProfile.md) / 主角配置
- [ProtagonistInputHandler](reference/ProtagonistInputHandler.md) / 主角输入处理器
- [FocusUi](reference/FocusUi.md) / 交互焦点 UI 控制器

### Level / 关卡

- Level / 关卡
- SpawnPoint / 出生点
- [LevelLoader](reference/LevelLoader.md) / 关卡加载器

### Mechanisms / 机制

- Behavioral Components / 行为组件
	- [Grabbable](reference/Grabbable.md) / 可抓取对象
	- [Detachable](reference/Detachable.md) / 可解体对象
- [Water](reference/Water.md) / 水体
	- [WaterProfile](reference/WaterProfile.md) / 水体配置
- [Waterlet](reference/Waterlet.md) / 水口
	- [WaterPump](reference/WaterPump.md) / 注水口
	- [WaterDump](reference/WaterDump.md) / 排水口
- [Loopshape](reference/Loopshape.md) / 回形
- [LoopshapeValidator](reference/LoopshapeValidator.md) / 回形检查器
	- [OpticalValidator](reference/OpticalValidator.md) / 光学回形检查器
	- [FocusValidator](reference/FocusValidator.md) / 准星回形检查器
	- [GrabbableValidator](reference/GrabbableValidator.md) / 可抓取回形检查器
- [PressurePlate](reference/PressurePlate.md) / 压力板（欲废弃）

### Utility / 工具

- [ArchitectureGenerator](reference/ArchitectureGenerator.md) / 建筑生成器
	- [MeshTile](reference/MeshTile.md) / 模型阵列
	- [ConcreteBox](reference/ConcreteBox.md) / 实心盒子
- [RigidbodySound](reference/RigidbodySound.md) / 刚体声音
- [StampHandler](reference/StampHandler.md) / 投射控制器
- [Carrier](reference/Carrier.md) / 载体
	- [DtCarrier](reference/DtCarrier.md) / 双掷载体
- [Logic](reference/Logic.md) / 场景逻辑
	- [DelayedLogic](reference/DelayedLogic.md) / 延时逻辑
- Statics / 静态类
	- [AudioUtility](reference/AudioUtility.md) / 声音工具
	- [LevelUtility](reference/LevelUtility.md) / 关卡工具
	- RenderUtility / 渲染工具