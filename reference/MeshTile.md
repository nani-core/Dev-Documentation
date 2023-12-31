# MeshTile

`MeshTile` 是用来在场景中批量铺设对象的工具组件类。
它允许开发者选择一个基础单位对象，在任意大小、朝向的平行多面体网格上批量铺设，并支持可自定义区域的镂空功能。

此工具组件铺设出来的对象在编辑模式下不可被选中。
进入运行模式时，此组件会销毁自身。

- 继承自：[`ArchitectureGenerator`](./ArchitectureGenerator.md)

## 序列化字段

- `GameObject tile`：铺设单元。
- `Vector3 i, j, k`：网格基准方向。
- `Vector3Int count`：网格在基准方向上重复的次数。
- `Vector3 uvw`：组件本身锚点在铺设结果中所处的位置比例。

	如若设置为 `(0, 0, 0)`，则起始角落里的对象与本组件对齐；
	又若设置为 `(1, 1, 1) / 2`，则网格中心与本组件对齐。

- `List<GameObject> hollowObjects`：铺设时应避开镂空的游戏对象。

	铺设时会检测选定对象里的所有 `Collider`，若格点处在碰撞范围内则会跳过生成。

	仅支持 `BoxCollider` 与 `SphereCollider`。