# Interactable

`Interactable` 是一切可交互组件的基类。
挂载此类组件的对象可以被主角的视线选中、并在交互时做出响应。

- 继承自：`MonoBehaviour`
- 必需组件：`Collider`

# 序列化字段

- `Rigidbody rigidbody`：此对象的 `Rigidbody` 组件，非必需。

	> 在编辑模式下，此字段会被自动设置。

- `UnityEvent onFocusEnter`：被主角视线选中时触发的事件。
- `UnityEvent onFocusLeave`：主角视线离开时触发的事件。
- `UnityEvent onInteract`：被主角交互时触发的事件。