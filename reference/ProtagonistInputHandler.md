# ProtagonistInputHandler

`ProtagonistInputHandler` 是用户输入与主角控制器之间的中间件。
它会根据主角控制器的输入规范与具体状态，将来自 [Input System](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/manual/index.html) 的消息与输入数据经过处理，送到正确的接口中去。
这样，主角控制器就与用户输入的实际形式解耦开来；任何组件都可以以同样方式操纵主角。

- 继承自：`MonoBehaviour`

> `ProtagonistInputHandler` 没有任何公有属性或方法，但它必须与 `Protagonist` 绑定在同一个对象上，并需要 `PlayerInput` 也绑定在同一个对象上以接收用户输入。

> `PlayerInput` 会发送 `On + [input action map 资产中定义的 action 名]` 的<u>消息</u>。注意不要写出重名方法导致被用户输入触发不期望的调用。