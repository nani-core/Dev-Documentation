# 开发文档

## Manual / 手册

- [生命周期总览](manual/life-cycle-overview.md)（待编撰）
- [交互](manual/interaction.md)
- [光学回形](manual/optical-loopshape.md)
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

### Mechanisms / 机制

- [Interactable](reference/Interactable.md) / 可交互对象
	- [Grabbable](reference/Grabbable.md) / 可抓取对象
	- Placement / 放置机会（未实现）
	- [Clickable](reference/Clickable.md) / 可点击对象
	- [Detachable](reference/Detachable.md) / 可解体对象
- [Water](reference/Water.md) / 水体
- [Floatable](reference/Floatable.md) / 可漂浮对象
- [Waterlet](reference/Waterlet.md) / 水口
	- [WaterPump](reference/WaterPump.md) / 注水口
	- [WaterDump](reference/WaterDump.md) / 排水口
- [LoopShape](reference/LoopShape.md) / 回形
	- ~~PositionalLoopShape / 基于位置的回形~~（已废弃）
	- [OpticalLoopShape](reference/OpticalLoopShape.md) / 光学回形
- [PressurePlate](reference/PressurePlate.md) / 压力板

### Utility / 工具

- [ArchitectureGenerator](reference/ArchitectureGenerator.md) / 建筑生成器
	- [MeshTile](reference/MeshTile.md) / 模型阵列
	- [ConcreteBox](reference/ConcreteBox.md) / 实心盒子
- [RigidbodySound](reference/RigidbodySound.md) / 刚体声音
- [SceneLoader](reference/SceneLoader.md) / 场景加载
- [StampHandler](reference/StampHandler.md) / 投射控制器
- [Carrier](reference/Carrier.md) / 载体
	- [DtCarrier](reference/DtCarrier.md) / 双掷载体
- [Logic](reference/Logic.md) / 场景逻辑
	- [DelayedLogic](reference/DelayedLogic.md) / 延时逻辑
- Statics / 静态类
	- [AudioUtility](reference/AudioUtility.md) / 声音工具
	- [SceneUtility](reference/SceneUtility.md) / 场景工具
	- RenderUtility / 渲染工具