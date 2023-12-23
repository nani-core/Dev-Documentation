# ArchitectureGenerator

`ArchitectureGenerator` 是用来程序化生成建筑结构的工具组件抽象基类。
将它绑定到 `GameObject` 上，即可以之为基变换生成想要的结构。

为了避免不必要的数据开销，`ArchitectureGenerator` 区分了编辑时与运行时的生成行为。
编辑时生成的结构将不会保存到场景中去，并且会在更新时销毁重建。
所有继承自 `ArchitectureGenerator` 的子类均可以通过实现接口方法来免费达到这种效果。

- 继承自：`MonoBehaviour`
- 编辑时行为特化