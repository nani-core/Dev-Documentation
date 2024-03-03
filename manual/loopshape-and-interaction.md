# 回形与交互

## 回形相关的程序设计

由于游戏设计的核心是「只要是回形就能交互」且「不是回形就不能交互」，回形实际上构成了游戏的唯一交互来源。
承载回形身份的类是 [Loopshape](../reference/Loopshape.md)。
它有一个 `onOpen` 的 `UnityEvent`，可以绑定回形“开启”时要触发的逻辑。

然而，回形并不是只要存在就可以触发的。
例如光学回形，必须要在岛和环在屏幕空间中满足构成回形图案的条件时才能够触发。
就算是最普通的“放在场景里”的静态回形，也要至少在玩家准星对准的时候才能触发。
因此，所有的 `Loopshape` 都有一个 `isValidated` 的 `bool` 属性。
只有当该属性为 `true` 时，玩家才能够与回形交互，进而触发之。

鉴于回形满足条件的类型多种多样，因此不宜直接在 `Loopshape` 这个承载类本身里面耦合检测满足条件的逻辑。
为此，设计了 [LoopshapeValidator](../reference/LoopshapeValidator.md) 的基类。
它与 `Loopshape` 的关系就像 `MeshFilter` 与 `MeshRenderer` 的关系，协同工作，由前者为后者提供数据来源。

与语义不同的是，`LoopshapeValidator` 并不必须与其作用的 `Loopshape` 挂载在同一 `GameObject` 上。
这主要是为了设计灵活性上的考虑，例如有的嵌套回形的场合必须这样操作。
`LoopshapeValidator` 有一序列化字段 `Loopshape loopshape`，可以指定作用的 `Loopshape`。
如果不需要特殊指定，置空即可。

一个 `Loopshape` 可以有多个 `LoopshapeValidator` 同时作用。
在这种情况下，多个 `LoopshapeValidator` 的满足条件是或的关系。
只要有一个满足，`Loopshape` 就可以触发。

`LoopshapeValidator` 作为抽象基类，有下面几种实现，分别对应不同类型的满足条件：

- [FocusValidator](../reference/FocusValidator.md)：在玩家准星落在物体上时满足。
- [GrabbableValidator](../reference/GrabbableValidator.md)：继承自 `FocusValidator`，但额外要求在玩家抓起物体时才满足。
- [OpticalValidator](../reference/OpticalValidator.md)：光学回形。可以指定岛与环物体。

## 玩家交互

在承担主角控制的 `Protagonist` 类中，维护了一个“当前满足的 `Loopshape`”的集合。
场景中的 `Loopshape` 在其 `LoopshapeValidator` 的满足条件成立/失败时，会将变动通知给 `Protagonist`；
后者即更新自己的集合。

在玩家做出交互操作时，会遍历上述 `Loopshape` 集合，依次触发其“开启”事件。
紧接着，若玩家正在抓取物体，则物体也会被放下。

这个系统可以实现「只要是回形就能交互」且「不是回形就不能交互」的核心设计。

## 行为组件

行为，是指玩家交互之后“会发生什么事”的最小构成单位。
其具体内容请看[设计文档/行为](https://github.com/nani-core/Design-Documentation/blob/master/mechanics/Behaviors.md)一章。

之前，行为由 [Interactable](../deprecated/reference/Interactable.md) 基类的子类来承担。
玩家在与挂载有 `Interactable` 组件的 `GameObject` 交互时，会主动触发其行为。

现在，此设计已经完全被废弃，`Interactable` 已经从项目中消失了。
取而代之的是新的基于 `Loopshape` 的交互系统。
原先所有 `Interactable` 的子类，现在退化为**提供行为**的被动组件；玩家交互时不会主动触发它们。
如果需要触发某种行为，则应当藉由 `Loopshape` 的 `onOpen` 事件，手动调用行为组件的接口方法。

目前有下面几种行为组件：

- [Grabbable](../reference/Grabbable.md)：抓起、放下。
- [Detachable](../reference/Detachable.md)：解体。

注意，设计文档中的「Floating / 漂浮」行为并不由行为组件来支持。
相反，任何刚体在水体里都会受到浮力。
可以通过调整刚体的质量来影响其密度，进而影响其漂浮行为。