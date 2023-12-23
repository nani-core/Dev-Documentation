# ConcreteBox

`ConcreteBox` 用来生成方形建筑结构。
开发者可以任意设置六个面的有无以及建筑的尺寸。
为了避免出现光照漏洞，此组件会自动在每个面埋一个防止漏光的方盒（水泥块）。

> 序列化字段里的「材质」与「生成」的部分将考虑重新设计成六个面的 `struct`，以便支持更多选项。
> 出于序列化数据丢失的考虑，未予实施。

- 继承自：[`ArchitectureGenerator`](./ArchitectureGenerator.md)

## 序列化字段

### 材质

- `GameObject tile`：铺设单元。

- `Material concreteMaterial`：水泥块的材质（用来控制光照效果）。

### 几何

- `Vector3Int count`：铺设单元在三个维度上的重复次数（建筑大小）。

- `Vector3 spacing`：单个铺设单元的尺寸。

- `float concreteThickness`：水泥块的厚度。

- `float concreteDepth`：水泥块埋的深度。

	这是为了避免水泥块与铺设单元发生 Z-fighting。

- `List<GameObject> hollowObjects`：镂空。

	见 [MeshTile/序列化字段](./MeshTile.md/#序列化字段)。

- `bool inward`：向外还是向内。

	若设为 `true`，则生成的铺设单元的 Z 轴朝外，内部实心；
	反之，则会生成一个类似房间的结构。

- `bool preventOverlapping`：防止角落重叠。

	为了实现防止漏光的目的，水泥块会比盒子的尺寸略宽，这可能导致角落上穿模。
	如果出现了这种情况，可以勾选此选项来避免。
	但是，这样做可能会导致漏光。

### 生成

- `bool xp`、`bool xm`、`bool yp`、`bool ym`、`bool zp`、`bool zm`：
	在六个方向上分别是否生成面。
	`p` 指正方向，`m` 指负方向，采用 Unity 的左手系。

	> 见开头的注释。