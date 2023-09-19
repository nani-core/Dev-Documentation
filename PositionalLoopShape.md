# PositionalLoopShape

`PositionalLoopShape` 是基于玩家视点与环和岛的对象的相对位置而判定的回形控制器类。

> 此类实际表现欠佳，将来会被废弃。

- 继承自：[`LoopShape`](LoopShape.md)

## 序列化字段

- `GameObject blasto`：岛。
- `GameObject gastro`：环。
- `Transform origin`：此回形判定方向上的最远点。
- `NoPivotCheeseSlice positioning`：此回形判定时玩家的站位条件。
- `PivotCheeseSlice placement`：此回形判定时岛的放置位置条件。

## 属性

- `Vector3 OriginPos { get; }`：回形判定最远点的位置。
- `Vector3 BlastoPos { get; }`：岛的位置。
- `Vector3 GastroPos { get; }`：环的位置。

## 方法

- `void DestroyGastro()`：使岛消失。

	此方法通过设置岛的 `GameObject.enabled` 属性来使之消失，而非直接销毁其 `gameObject`。